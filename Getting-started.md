Before you read this guide, you might want to read the
[Installation](Installation) page.

Ketting is a client for hypermedia APIs. This is a flavour of APIs that, among
other things uses links to express relationships and for clients to navigate
from endpoint to endpoint.

If you are using one of those APIs, then Ketting might be a good HTTP client to
interfact with it.

Ketting specifically understands links from the following formats:

* HTML links. It can pick up links from [`<a>`][html-a] or [`<link>`][html-link]
  tags, as long as they have a have a `rel` and a `href` attribute.
* [Hal][hal]
* [Siren][siren]
* [JSON:API][jsonapi]

It also understands [HTTP Link headers][weblinking].

Following links
---------------

So how does this work? Say, we're working with an API that has the following
resources:

    https://api.example/ <- main document that has a link with rel=article-collection
    https://api.example/articles <- contains one or more links with rel=item
    https://api.example/articles/1 <- contains a link with rel=author
    https://api.example/author/mihok

Above we have a chain of links, and we want to get from the API home to
fetch information about an author. We can use ketting as follows:


```typescript
const ketting = new Ketting('https://api.example');
const homeResource = ketting.go();

const authorResource = await homeResource
  .follow('article-collection')
  .follow('item')
  .follow('author');

console.log(await authorResource.get());
```

Here we followed the entire chain of links to ultimately get to the author
resource. Finally we do a `GET` request to get the body.

[Read the docs on follow() and followAll()](Following-Links)

Resources and HTTP requests
---------------------------

The resource object is really important in Ketting. It's an object that points
to a url, and has a couple of functions.

If you `await` the result of a `follow()` function, or if you call a `go()`
function, you get a resource back.

This resource has a few functions that all map to HTTP requests.

```typescript
// Does a GET request and returns the body
const body = await resource.get();

// Updates the resource with PUT
await resource.put({foo: 'bar'});

// Issues a DELETE request
await resource.delete();

// Issues a POST request
await resource.post({foo: 'bar'});

// Issues a PATCH request
await resource.patch({foo: 'bar'});
```

The `post` function is a bit special. HTTP `POST` is often used to create new
resources. When this happens, typically APIs return:

* `201 Created`
* A `Location` HTTP header pointing to the newly created resource.

When both of these are true, the `post()` function will return a new resource
object:

```typescript
const newResource = await resource.post({foo: 'bar'});
console.log(await newResource.get());
```

If you want to issue a completely custom HTTP request, perhaps to use a special
http method, headers or different kind of request body, the Resource object also
has a `fetch()` method.

This `fetch()` method is similar to the [Fetch API][fetch] in browsers. There's
2 main differences:

1. You don't need to specify a URL. So the url argument can be skipped.
2. If a URL is specified, you can specify a relative url. The relative url will
   be applied to the URL of the current resource.

```typescript
const response = await resource.fetch({method: 'SEARCH'});
```

Lastly, the `Resource` object has a `fetchAndThrow()` method. This method works
identical to `fetch()`, except it will throw an exception if the request
returned a `4xx` or `5xx` status code.

Resources and Links
-------------------

Resources have 2 functions to follow links:

```typescript
const newResource = await resource.follow('rel');
const manyResources = await resource.followAll('rel');
```

Aside from that, it also has a few functions to just get information about links:

```typescript
const links = await resource.links('rel');
const link = await resource.link('rel');
```

The reason these are both `async` functions, is because Ketting will not
automatically grab a resource's request body. It will wait until it is
absolutely needed to do so, so when `link` or any other link-related method
is called, it will fetch the request body if it didn't have it already.


Other functions on resources
----------------------------

### uri

To get the uri of the current resource, use the uri property

```typescript
console.log(resource.uri);
```

### go

Sometimes a resource doesn't have a link, and you just need to get a new
resource via a relative link.

This can be done with the `go()` function. The `go()` function returns a
new resource based on a relative (or absolute) url.

```typescript
const newResource = resource.go('?sort=descending');
```

The `go()` function is one of the few that's not asynchronous. This is
possible, because `go()` doesn't need to do any HTTP requests to create the
new resource.

### refresh

Ketting keeps an internal cache of every resource it ever received. This means
that if you call `get()` twice, it only does a HTTP request the first time.

This is even true when you call the second `get()` before the first one
completed, as it also keeps track of any in-flight requests.

The only times ketting expires this cache are:

* When you call an unsafe method, such as `delete()`, `post()` or `patch()`.
* If you did an HTTP request on an another resource, and that resource
  returned a HTTP links such as `Link: </foo>; rel="invalidates"`.
* If you call the `refresh()` method.

The `refresh()` method on resources works the exact same way as `get()`,
except that it will always get a new copy of the resource from the serve.

```typescript
// Do the first request
console.log(await resource.get());

// After a few minutes something may have changed on the server.
// Lets get a fresh copy
console.log(await resource.refresh());
```

Note that this is _not_ needed after you did for example a `PUT` request.
In that case Ketting will automatically expire its cache.

[html-a]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a
[html-link]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link
[hal]: https://tools.ietf.org/html/draft-kelly-json-hal-00
[siren]: https://github.com/kevinswiber/siren
[jsonapi]: https://jsonapi.org/
[weblinking]: https://tools.ietf.org/html/rfc8288
[fetch]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
