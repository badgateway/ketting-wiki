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
// Does a GET request and returns a 'State' object with a 'data' property that
// contains the parsed response body.
const state = await resource.get();
console.log(state.data);

// Updates the resource with PUT
await resource.put({
  data: {
    foo: 'bar'
  }
});

// Issues a DELETE request
await resource.delete();

// Issues an RPC-style POST request
await resource.post({
  data: {
    foo: 'bar'
  }
});

// Creates a new resource with POST.
//
// If the server returns 201 Created and a Location header, a new resource
// object is returned.
const newResource = await resource.postFollow({
  data: {
    foo: 'bar'
  }
});

// Issues a PATCH request
await resource.patch({
  data: {
    foo: 'bar'
  }
});
```

If you want to issue a completely custom HTTP request, perhaps to use a special
http method, headers or different kind of request body, the Resource object also
has a `fetch()` method.

This `fetch()` method is similar to the [Fetch API][fetch] in browsers, but it does
not have a 'url' argument.

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

If you want more information about the links that the resource currently has,
you can get to this via the State object.

```typescript
const state = await resource.get();

const link = state.links.get('rel');
const links = state.links.getMany('rel');
```

Events
------

### 'update' event

This event will get triggered whenever a new State is received
from the server, either through a `GET` request or if it was
transcluded.

It will also trigger when calling `PUT` with a full state object,
and when `updateCache()` was used.

```typescript
resource.on('update', state => {

  console.log('We got a new body for this resource!');
  console.log(state.data);

});
```

### 'stale' event

Whenever an unsafe HTTP method was used, the cache expires. When this happens,
a 'stale' event gets emitted.

```typescript
resource.on('stale', => {

  console.log('Cache is stale, lets get a new body');
  resource.refresh();

});
```

### 'delete' event

This event gets triggered when the resource is deleted. It could be useful
to notify a user.

```typescript
resource.on('delete', => {

  console.log('Resource is bye bye');

});
```

Managing the cache
------------------

Ketting by default has a pretty aggressive cache, and will not expire anything
unless explictly asked for.

It's possible to do this by calling `clearCache` on the resource.

```typescript
resource.clearCache();
```

It's also possible to update the local state cache. This can be helpful in
frontend applications to emit the resource state to all listeners, and makes
frameworks like Redux not as needed.

```typescript
// Update the cache and emit 'update' events.
resource.updateCache({data: { foo: 'BAR!'}});
```

If the aggressive 'forever' cache is not desired, it's possible to swap it out
for a cache that only keeps State objects for 30 seconds:

```typescript
const client = new Client('https://api.example.org');
client.stateCache = new ShortCache();
```

There is also a `NeverCache` but this is not recommended to use unless you really
know what you're doing or you're testing. Not having a cache at all wrecks a lot
of optimizations.


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
