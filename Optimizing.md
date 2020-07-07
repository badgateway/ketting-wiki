*Note: it's strongly advisable to read [Hypermedia](Hypermedia),
as this page builds upon all the established concepts there.*

With Hypermedia APIs, it's good design to have many resources that
are all identifiable by a URI.

We will go back to our 'Collection of articles' example:

```json
{
  "_links": {
    "item": [
      { "href": "/articles/1" },
      { "href": "/articles/2" },
      { "href": "/articles/3" }
    ],
    "next": { "href": "/articles?page=2" }
  },
  "total": 25
}
```

To output bodies from all these articles, you might want to do this:

```typescript
// 'followAll' returns an array of resources
const articleResources = await articleCollection.followAll('item');

for(const resource of articleResources) {
  const state = await resource.get();
  console.log(state.data);
}
```

If nothing was done to optimize this and nothing is cached, this will
result in a `GET` request for each article in sequence.

Because we used `await`, it will wait for a request to complete before
starting the next one.

Based on this example, we're going to go over all the different ways
this may be optimized.

Parallelize
-----------

A pure Javascript rewrite that will make these requests happen in parallel,
is as such:

```typescript
const articleResources = await articleCollection.followAll('item');

const promises = [];
for(const resource of articleResources) {
  promises.push(resource.get());
}

for(const state of await Promise.all(promises)) {
  console.log(state.data);
}
```

This will cause all requests to be fired at the same time. This can cause
a decent speed boost in HTTP/1.1, but an incredible speed boost with HTTP/2.

We successfully deployed APIs that can do hundreds of these and barely slow
down.

However, there's a cleaner way to write this.

Prefetch
--------

The following example will have an _identical_ effect, but you can write
code more linearly.

```typescript
const articleResources = await articleCollection
  .followAll('item')
  .prefetch(); // This is the secret ingredient

for(const resource of articleResources) {
  const state = await resource.get();
  console.log(state.data);
}
```

Adding `.prefetch()` to `followAll()` will fire off all the parallel HTTP/2
requests in the backend immediately, so by the time you `await`, a rqeuest
is already underway. Ketting de-duplicates identical `GET` requests that are
happening in parallel.

`prefetch()` will also not fire off requests if there was already a cached
state

HTTP/2 is great and very fast. If the performance of your application is good
enough, it is preferred to do more HTTP requests and try to write your
application that it can do a lot of these.

But perhaps you need to support HTTP/1.1, or perhaps your per-request
overhead is high and worth eliminating. If this is the case, read on.

Embedding resources
-------------------

Also known as 'Compound requests' or 'transcluding', embedding is a technique
that allows a single response with `GET` to return data from other
resources.

HAL, Siren and a few other formats have a way to embed resources resource. In
HAL this is done via an `_embedded` property.

Here's an example of an article collection with 2 articles embedded:

```json
{
  "_links": {
    "item": [
      {"href": "/article/1"},
      {"href": "/article/2"}
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

One benefit of using this technique is that it's entirely server-controlled.
If you see a hot path, the server can optimize this by embedding related
resources, and your client does not need to change to instantly take
advantage of this optimization.


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

### Reading list

1. [Let's Stop Building APIs Around a Network Hack][3] - Phil Sturgeon
2. [Performance testing HTTP/1.1 vs HTTP/2 vs HTTP/2 + Server Push for REST APIs][2] - Evert Pot

[1]: https://tools.ietf.org/html/draft-kelly-json-hal
[2]: https://evertpot.com/h2-parallelism/
[3]: https://tools.ietf.org/html/draft-pot-prefer-push
[4]: https://github.com/inadarei/draft-prefer-transclude/blob/master/draft.md 
[5]: https://apisyouwonthate.com/blog/lets-stop-building-apis-around-a-network-hack
