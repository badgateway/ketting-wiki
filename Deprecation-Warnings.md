If your API has endpoints that are scheduled for deprecation, or are
deprecated, Ketting can emit warnings in the console, so they are more
likely spotted by a developer.

Deprecating Endpoints/Resources
-------------------------------

There's currently work done on a new internet standard:
`draft-cedik-deprecation-header`, a.k.a.:
["The Deprecation HTTP Header Field"][2].

The way this works is that the server may emit a header such as one of these:

```http
Deprecation: Mon, 1 Nov 2021 00:00:00 GMT
Deprecation: true
```

If a server emits these, it tells the client that the endpoint should no
longer be used, or will be removed at a future date.

If specified, Ketting will now send warnings to the console via `console.warn`,
making it easier to spot reliance on deprecated endpoints.

The draft also defines the following additional headers:

```http
Sunset: Wed, 1 Dec 2021 00:00:00 GMT
Link: </docs/update-2021>; rel="deprecation"
```

These headers allow a server to tell a client when the endpoint will stop
responding, and point to additional information about the depreciation.

If either of these are specified, Ketting will provide this information in
the console.


Deprecating links
-----------------

Aside from entire resources being deprecated, individual links may also get
deprecated. Given a HAL document, this may look like the following:

```json5
{
  _links: {   
    next: {
      href: '/next-page',

      hints: {
        status: 'deprecated'
      }
    }
  }
}
```

The format for 'hints' is documented in [draft-nottingham-link-hint][3].

When you follow the `next` link with Ketting, Ketting will now also emit
a console warning.

```typescript
// Emits warning
const nextResource = await resource.follow('next')
```


[2]: https://tools.ietf.org/html/draft-cedik-deprecation-header
[3]: https://tools.ietf.org/html/draft-nottingham-link-hint-02 HTTP Link Hints
