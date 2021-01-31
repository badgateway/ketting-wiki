If Ketting is used in a browser, and the API you're using is hosted on a
different domain, this is a good set of CORS headers that allow you to
use every feature.

```http
Access-Control-Allow-Origin: [yourdomain]
Access-Control-Allow-Headers: Content-Type, User-Agent, Authorization, Accept, Prefer, Link
Access-Control-Allow-Methods: DELETE, GET, PATCH, POST, PUT, HEAD
Access-Control-Expose-Headers: Location, Link
```

You might want to customize these for your specific purposes. A good rule
of thumb is to only add things to these lists as you need them.

Here's a breakdown of how each request header is used:

* `Authorization` - Only used if Authentication is on.
* `Accept` - Sent with every `GET` request.
* `Content-Type` - Sent with every `PUT`, `PATCH` and `POST` request.
* `Link` - Set to `Link` to provide a means for serialising one or more links in HTTP headers. `Link: < uri-reference >; param1=value1; param2="value2"`
* `Prefer` - Set to `Prefer: transclude="rel1, rel2"` as a hint to the server
  that it might want to embed linked resources for optimization. See
  [Prefer-Transclude][2].
* `Prefer-Push` - Set to `Prefer-Push: rel1, rel2` as a hint to the server
  that the client might want to fetch those resources next, so that it can
  do a HTTP/2 push for them. See [Prefer-Push][1]
* `User-Agent` - Set to `ketting/[version]` and sent with every request.

Response headers:

* `Location`. Ketting will attempt to read the `Location` header from a
  `201 Created` response to a `POST` request to find a newly created
  resource.

[1]: https://tools.ietf.org/html/draft-pot-prefer-push-01
[2]: https://inadarei.github.io/draft-prefer-transclude/
