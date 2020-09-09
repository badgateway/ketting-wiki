Ketting version 1 to 5 was relatively stable, but Ketting 6 introduces larger
changes. Many of these changes were made to fix long-standing architecture
issues, and open the door to new features and strong integration with Front-
end frameworks such as React.

What's new
----------

A non-exhaustive list of new features:

* A [react-ketting][1] package with deep React integration via
  Hooks.
* Multiple cache strategies, such as `forever`, `short` and `never`.
* Support for fetch-middlewares. OAuth2 is reimplemented as such a plugin.
  these plugins can be added globally, or per-origin.
* `get()` now returns a `State` object, and functions such as `put()` will
  require one as an argument.
* `put()` now automatically updates the state cache.
* Support for `HEAD` requests and following links from `HEAD` response
  headers.
* It's now possible to set `Content-Type` and other headers on every
  resource method such as `Resource.post()`, `Resource.patch()`, etc.
* `update`, `stale` and `delete` events on Resources.
* PKCE support for OAuth2.
* Links can now be mutated and sent back to the server.
* Support for submitting HTML forms, Siren and HAL Forms (experimental).
* Nested transcluded items/embeds.
* A separate `post()` and `postFollow()` method.
* Better support for binary responses and `text/*` responses.

What's changed?
---------------

### State objects

By far the largest change is the use of `State` objects. In Ketting 5 and
below, you would get a parsed HTTP response when calling `get()`.

```typescript
// Ketting 5
const body = await resource.get();
```

The result of `.get()` is now a `State` object. To get the response body,
you need to get it from the `.data` property.

```typescript
// Ketting 6
const state = await resource.get();
const body = state.body;
```

Similarly, when doing a `PUT` request, you need also wrap your body:

```typescript
// Ketting 5
await resource.put({
  title: 'Hello world'
});

// Ketting 6
await resource.put({
  data: {
    title: 'Hello world'
  }
});
```

You might ask why. We wanted the ability to get more information from
responses, and pass more information when doing requests. Implementing this
in a BC way would have been a pain and make for an ugly API.


The State object adds a ton of data that would otherwise have been difficult
to get to:

* `State.data` - The response data.
* `State.uri` - URI of the resource
* `State.links` - List of all links related to the response.
* `State.contentType` - Content type string
* `State.contentHeaders` - HTTP Headers related to the content.
* `State.action()` - Execute actions such as submitting HTML forms or submit
   Siren actions.
* `State.serializeBody()` - Return a serialized version of the body.


Another design goal was that the `State` object should entirely encapsulate
state synchronous, so without the use of promises or async/await. It's all
there. This makes it much easier to use in functional programming paradigms,
and modern frontend frameworks.

It also allows users to for example: Get state, add a (hal-) link and submit
the result again:

```typescript
// Ketting 6
const state = await resource.get();
state.links.add('author', 'Dr. Pidgin');
await resource.put(state);
```

Lastly, there's a subscription framework related to states. When Ketting
'knows' of a new state, it will emit an `update` event.

```typescript
// Ketting 6
resource.on('update', (state: State) => {
  // We got a new State
  // Either caused by a `PUT` request, a `GET` response, or maybe the
  // resource was embedded in another resource's response.
});
```

### Depreciations

The following functions are now deprecated:

* `Resource.hasLink()`
* `Resource.links()`
* `Resource.link()`

They will be removed in a future major Ketting release.

This is how you migrate:

```typescript
// Ketting 5
const link = await resource.link('rel');
const links = await resource.links('rel');
const hasLink = await resource.hasLink('rel');


// Ketting 6
const state = await resource.get();

const link = state.links.get('rel');
const links = state.links.getMany('rel');
const hasLink = state.links.has('rel');
```

Once you have a `State` object, you get access to all the link information
syncronously.

In Ketting 6 you can also do the same with a `.head()` request. If links
are in the HTTP headers of the response to `HEAD`, they're all there.

### `getResource()` is removed

The `Client.getResource(uri)` and `Resource.getResource(uri)` were used to get
a resource based on a (potentially relative) uri.

This function was renamed to `.go()` some time ago:

Just search and replace `getResource()` to `go()` and you're good to go.


### Changes to `.post()`

In REST apis, `POST` typically has 2 major functions:

1. To submit an action or a form (RPC style).
2. To create a new resource.

It was hard to make a easy-to-use function to cover both cases, especially
since the return types of each may be different.

In Ketting 6, the old `post()` function is now split in 2 new functions:

* `.post()` for RPC style submission. This returns a `State` object, which has
  the response body and other information.
* `.postFollow()` for 'create' actions.

I suspect that most uses of `.post()` need to be migrated to `.postFollow()`.
Here's how it works:

```typescript
// Ketting 6
const newResource = await parentResource.postFollow({
  data: {
    title: "New blog post!",
  }
});
```

`newResource` in the above example will be the brand new resource that you
just created. It works because if the server returns a `201 Created` status,
and a `Location` header, it knows that a new resource was created and where
it lives.

If the server returned a `204 No Content` or `205 Reset Content` response,
`.postFollow()` will simply return the current resource again.


### Authentication changes

In the past, to set up Ketting with OAuth2 or Basic auth, this was
accomplished via a complex settings object in the Ketting constructor:

```typescript
// Ketting 5
import { Client } from 'ketting';

const client = new Client(
  'api.example.org',
  {
    auth: {
      type: 'basic',
      userName: 'foo',
      password: 'bar'
    }
  }
);

const client = new Client(
  'api.example.org',
  {
    auth: {
      type: 'oauth2',
      grant_type: 'authorization_code',
      clientId: 'fooClient',
      code: '...',
      tokenEndpointUri: 'https://api.example.org/oauth/token',
    }
  }
});
```

In Ketting 6, auhtentication is handled via plugins, or Fetch middlewares.

```typescript
// Ketting 6
import { Client, basicAuth, oauth2 } from 'ketting';

const client = new Client('api.example.org');

client.use(basicAuth({
  userName: 'foo',
  password: 'bar'
});

client.use(oauth2({
  grant_type: 'authorization_code',
  clientId: 'fooClient',
  code: '...',
  tokenEndpointUri: 'https://api.example.org/oauth/token',
});
```

To only set up authentication for a single domain (origin), use the second
argument of `use()`

```typescript
// Ketting 6
client.use(oauth2({
  grant_type: 'authorization_code',
  clientId: 'fooClient',
  code: '...',
  tokenEndpointUri: 'https://api.example.org/oauth/token',
}, 'api.example.org');
```

Wildcards are supported here for domain-wide authentication:

```typescript
// Ketting 6
client.use(oauth2({
  grant_type: 'authorization_code',
  clientId: 'fooClient',
  code: '...',
  tokenEndpointUri: 'https://api.example.org/oauth/token',
}, '*.example.org');
```

### Questions?

If you run into issues, we would love to hear from you. We want the docs to be
as good as possible, so please [open a ticket][2].

[1]: https://github.com/badgateway/react-ketting
[2]: https://github.com/badgateway/ketting/issues
