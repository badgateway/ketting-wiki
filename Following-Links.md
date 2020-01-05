The main way to traverse APIs with Ketting is through following links.

Getting your first resource
---------------------------

To start using an API, you need to grab the home resource.

```typescript
const ketting = new Ketting('https://my-api.example');
const homeResource = ketting.go();
```

The resource has functions like `.put()`, `.get()`, `.post()` and others.
It also has `.follow()` and `.followAll()` for following links.

Following a link from a resource
--------------------------------

Lets say that your home resource has a link with relationship 'author', you
can get to this resource with the `follow()` function.

```typescript
const authorResource = await homeResource.follow('author');
```

`follow()` returns a new resource, that has all the same methods from the
original resource.

For this to work, the home resource needs to return a document like this:

```json
{
  "_links": {
    "author": {
      "href": "https://my-api.example/author"
    }
  }
}
```

The above example is [HAL][1], but it could also be one of the other supported
types. For example, if the home resource returned HTML, it would also work
transparently:

```html
<html>
  <head>
    <title>Welcome to the API</title>
    <link rel="author" href="https://my-api.example/author" />
  </head>
</html>
```

Ketting doesn't care what format your document is, as long as it's one of the
many supported hypermedia formats. `follow()` just follows links.

Chaining follow
---------------

It's also possible to immediately jump from link to link by chaining
`follow()`.

```typescript
const articleResource = await resource.follow('author').follow('article');
```


Getting a collection of links
-----------------------------

In hypermedia formats, usually a collection of things (like a list of articles)
is represented by multiple `item` links.

If our home document had a link to a `article-collection`, and in that
collection is 1 `item` link per article, we can get them with `.followAll()`.

The following example fetches many `item` links and also puts each article
in the javascript console.

```typescript
const articleCollection = await homeResource.follow('article-collection');
const articleResources = await articleCollection.followAll('item');

for(const articleResource of articleResources) {
  console.log(await articleResource.get());
}
```


Getting information about links
-------------------------------

Resources have a few extra functions that can help you get link data.

```typescript

// Return 1 link or throw exception
const link = await homeResource.link('article-collection');

// Return 0 or more links
const links = await articleCollection.links('item');

// Return true or false
const linkExists = await homeResource.hasLink('author');
```

Pre-fetching many objects
-------------------------

Our previous example had this line to get a list of articles:

```typescript
const articleResources = await articleCollection.followAll('item');
```

Later on, we fetch each article's body:

```typescript
for(const articleResource of articleResources) {
  console.log(await articleResource.get());
}
```

One issue is that it grabs every article in sequence, which can take a long
time.

There's a few ways to remedy this.

### Embedding resources

HAL, Siren and a few other formats have a way to 'embed' a resource. In HAL
this is done via an `_embedded` property.

Here's an example of an article collection with 2 articles embedded:

```json
{
  "_links": {
    "item": [
      {"href": "https://my-api.example/article/1"},
      {"href": "https://my-api.example/article/2"}
    ] 
  },
  "_embedded": {
    "item": [
      {
        "_links": {
          "self": { "href": "https://my-api.example/article/1" }
        },
        "title": "Welcome to my blog!",
        "body": ".."
      },
      {
        "_links": {
          "self": { "href": "https://my-api.example/article/2" }
        },
        "title": "Second post!",
        "body": ".."
      }
    ]
  }
}
```

If Ketting sees these embedded resources, it will automatically parse
and cache them.

So you don't need to change your loop:

```typescript
for(const articleResource of articleResources) {
  console.log(await articleResource.get());
}
```

Because everything was embedded, ketting will not do actual HTTP requests,
but instead will serve the items really fast from it's internal cache.

Automatically parsing embedded items is supported for any format that has
this concept.


### Pre-fetching

If items were not embedded, it's possible to instruct Ketting to immediately
pre-fetch items in the background.

Here's the same example again, but with pre-fetch:

```typescript
const articleResources = await articleCollection
  .followAll('item')
  .preFetch();

for(const articleResource of articleResources) {
  console.log(await articleResource.get());
}
```

With the new `preFetch()` function, everything gets fetched immediately. The
HTTP requests get fired off in the background in parallel which often is _much_
faster.

### Sending Prefer-Push

When fetching a collection, it's also possible to send a [Prefer-Push][3] header.
This can instruct the server to do a HTTP/2 Server Push for linked resources.

Sending this header automatically can be done on the `follow()` or
`followAll()` result:

```typescript
const articleCollection = await homeResource
  .follow('article-collection')
  .preferPush();
```

When ketting grabs the initial collection, it will send this header:

```http
GET /article HTTP/1.1
Host: my-api.example
Prefer-Push: item
```

If the server supports this feature, it will initiate a HTTP/2 push for each
item. It will be ignored by servers that don't support it.

### Sending Prefer: transclude=...

Very similarly, it's possible to send a [`Prefer: transclude=item`][4] header:

```typescript
const articleCollection = await homeResource
  .follow('article-collection')
  .preferTransclude();
```

This instructs the server to 'please embed all the items with this link
relationship'.

This also only works if the server supports this feature.

### More info

If you'd like to know more about optimizing fetching of request, the author of
library has also wrote a [big article][2] about performance testing different
approaches.


[1]: https://tools.ietf.org/html/draft-kelly-json-hal
[2]: https://evertpot.com/h2-parallelism/
[3]: https://tools.ietf.org/html/draft-pot-prefer-push
[4]: https://github.com/inadarei/draft-prefer-transclude/blob/master/draft.md 
