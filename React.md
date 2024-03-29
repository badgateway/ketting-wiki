*Note: it's advisable to read [Getting Started](Getting-Started)
first, as this page builds upon all the established concepts there.*

If you use Ketting with [React][1], Ketting ships with a bunch of
React bindings that make developing a lot easier.

The API is heavily inspired by [Apollo Client][4], and should be
familiar if you've used it in the past.

Installation
------------

    npm i ketting react-ketting

Examples
--------

In the following examples, we are assuming that the following HTTP requests
are available:

    POST https://api.example/article - Create a new article
    GET  https://api.example/article/1 - Retrieve an article
    PUT  https://api.example/article/1 - Update an article

Articles have the following general structure:

```json
{
  "title": "Hello world!",
  "body": "First post"
}
```

### Application setup

It's recommended to use the `<KettingProvider>` component at the top of your
application. It's not required for most features, but it makes some examples
easier.

```typescript
import React from 'react';
import { render } from 'react-dom';
import { Client } from 'ketting';
import { KettingProvider } from 'react-ketting';

// Create a new client, and set the base uri for the API.
// This URI will be used to resolve any relative uris.
const client = new Client('https://api.example/');

const App = () => (
  <KettingProvider client={client}>
    <ArticleView />
  </KettingProvider>
);

render(<App />, document.getElementById('root'));
```

### Viewing an article

Lets develop the `<ArticleView>` component.

```typescript
import { useResource } from 'react-ketting';

/**
 * Ideally you will want to generate this from a JSON Schema, or
 * OpenAPI definition.
 */
type Article = {
  title: string;
  body: string;
}

function ArticleView() {

  const { loading, error, data } = useResource<Article>('/article/1');
  if (loading) return <p>Loading...</p>;
  if (error) return <div className="error">{error.message}</div>;

  return <article>
    <h1>{data.title}</h1>
    <p>{data.body}</p>
  </article>;

}
```

Here `useResource` returns a few properties:

* `loading` - will turn to true as soon as loading is complete, or there was an error.
* `error` - will have a Javascript `Error` object.
* `data`- The data received from the server.


### Editing an article

Lets try a more advanced example. The following allows a user to make changes
to the body. For brevity the title is not changable.

```typescript
import { useResource } from 'react-ketting';

/**
 * Ideally you will want to generate this from a JSON Schema, or
 * OpenAPI definition.
 */
type Article = {
  title: string;
  body: string;
}

function ArticleView() {

  const { loading, error, data, setData, submit } = useResource<Article>('/article/1');
  if (loading) return <p>Loading...</p>;
  if (error) return <div className="error">{error.message}</div>;

  const handleChangeBody = (ev: React.FormEvent<any>) => {
    setData({
       ...data,
       body: ev.target.value
    });
  }

  const handleSubmit = async () => {

    await submit();

  }

  return <article>
    <h1>{data.title}</h1>
    <p><textarea onChange={handleChangeBody} value={data.body}</textarea>
    <input type="submit" onclick={handleSubmit} value="Save" />
  </article>;

}
```

A few new properties were returned from `useResource`.

* `setData()` updates the internal cache for the resource. One thing to note
  is if you use the same resource (with the same URI) in different components,
  all of them will receive an automatic state update.
* `submit()` when you are all done, `submit()` will turn your Article in a JSON
  object and send it to the server with `PUT`.


### Creating a new article.

Creating a new article is almost identical, the only difference is in the
first few lines:

```typescript
function ArticleView() {

  const { loading, error, data, setData, submit } = useResource<Article>({
    resource: '/article/',
    mode: 'POST',
    initialState: {
      title: 'New post!',
      body: 'Enter your content here',
    },
  });
  if (loading) return <p>Loading...</p>;
  if (error) return <div className="error">{error.message}</div>;
  
  /* Etc */
}
```

Of note is that you now pass an object to useResource. This object will
have the following properties:

* `resource` Where to send the request to
* `mode` Can be POST or PUT.
* `initialState` - The 'template'. Not too different from the argument to
  [useState()][5].
* `refreshOnStale` - If specified, the client will automatically do a `GET`
  request if the resource data is stale.

When `submit()` is eventually called, Ketting will send a `POST` request
to your server with the request body.

If the server responded with a [`201 Created`][6] header and a [`Location`][7]
header, Ketting will automatically follow that header and do a `GET` request
there to inspect the new state, causing an update to `data` as well.

Any subsequent calls to `submit()` will not do new `POST` requests. Instead,
it will do `PUT` requests to the newly created resource.

API Documentation
-----------------

### useResource

The useResource hooks manages the entire lifecycle of the state of a resource.
A resource typically refers to something with a single url.

To call it, you must pass a url, or a resource object.

Resource objects can be obtained from the ketting client or via other resources
through following hyperlinks.

Examples:

```typescript
const { loading, error, data } = useResource('/article/1');
const { loading, error, data } = useResource({
  resource: '/article/'
  mode: 'POST',
  initialState: { foo: 'bar' },

  // Optional
  refreshOnStale: true,
});


// Or with the Ketting client.
const client = useClient();
const resource = client.go('/article/1');
const { loading, error, data } = useResource(resource);

// Or as the result of a promise
const client = useClient();
const resource = client.go('/article/1');
const { loading, error, data } = useResource(resource.follow('author'));
```


Return values:

* `loading` - Will turn to true as soon as loading is complete, or there was an
  error.
* `error` - Will have a Javascript `Error` object.
* `data`- The data received from the server.
* `setData(data: T)` Updates the internal cache for the resource. One thing to
  note is if you use the same resource (with the same URI) in different
  components, all of them will receive an automatic state update.
* `submit()` - When you are all done, `submit()` will turn your Article in a
  JSON object and send it to the server with `PUT`.
* `resourceState` - A more complete complex version of the `data` property. It
  will also have some HTTP response headers, access to links (from the `Link`
  header, or from the body if the format was HAL, JSON:API, Siren,
  Collection+JSON, etc.
* `setResourceState` - Similar to setData, but needs an entire Ketting State
  object.

### useCollection

The `useCollection` hook allows you to get a list of resources
inside a collection.

This hook makes a few assumptions:

1. The collection is some hypermedia document, such as HAL, HTML, Siren,
   or anything Ketting supports.
2. The collection lists its members via 'item' web links.

Example call:

```typescript
const {
  loading,
  error,
  items
} = useCollection<Article>(resource);
```

The resource may be passed as a `Resource` object, a `Promise<Resource>`, or a
uri string.

Returned properties:

* loading - will be true as long as the result is still being fetched from
            the server.
* error - Will be null or an error object.
* items - Will contain an array of resources, each typed `Resource<T>` where
          `T` is the passed generic argument.

Bigger example:

```typescript
function MyCollection() {

  const {
    loading,
    error,
    items
  } = useCollection<Article>('/articles');

  if (loading) return <div>loading...</div>;
  if (error) return <div class="error">boo</div>;

  return <ul>{items.map(item => <MyCollectionItem resource={item} />)}</ul>

}

function MyCollectionItem({resource}: { resource: Resource<Article> }) {
  const {
    loading,
    error,
    data
  } = useResource(resource);

  if (loading) return <div>loading...</div>;
  if (error) return <div className="error">boo</div>;

  return <li>{data.title} - {data.body}</li>;

}
```

`useCollection` has a `refreshOnStale` option as well. When specified, Ketting
will automatically refresh the collection state if the current representation
was stale.

One example of this, is when an unsafe HTTP request is sent to the collection,
for example a `POST` request to add a new member.

After that request succeeds, stale events are emitted and this option will
cause Ketting to go to the server, fetch the new state and re-render.


### useClient

Gives you direct access to the Ketting client. For this to work, the
`KettingProvider` must be set up.

Examples:

```typescript
const client = useClient();
```

The client allows you to get direct access to Ketting Resource objects:

```typescript
const resource = client.go('/foo/bar');
```

If your API uses Web Links on the home document, you can also follow these
links to find resources:

```typescript
const resource = client.follow('article-collection');
```

You can also setup Fetch middlewares:

```typescript
client.use( (request, next) => {

  request.headers.set('Authorization', 'Bar');
  return next(request);

});
```

Or use one of the built-in advanced middlewares:

```typescript
import { oauth2 } from 'ketting';

client.use(oauth2({
  grantType: 'authorization_code',
  clientId: 'fooClient',
  code: '...',
  tokenEndpoint: 'https://api.example.org/oauth/token',
});
```

[1]: https://reactjs.org/
[2]: https://reactjs.org/docs/hooks-intro.html
[3]: https://github.com/badgateway/ketting
[4]: https://www.apollographql.com/docs/react/
[5]: https://reactjs.org/docs/hooks-state.html
[6]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/201 "201 Created status code"
[7]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Location "Location header"
