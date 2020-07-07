```typescript
class Client {

  /**
   * All relative urls will by default use the bookmarkUri to
   * expand. It should usually be the starting point of your
   * API
   */
  bookmarkUri: string;

  /**
   * Supported content types
   *
   * Each content-type has a 'factory' that turns a HTTP response
   * into a State object.
   *
   * The last value in the array is the 'q=' value, used in Accept
   * headers. Higher means higher priority.
   */
  contentTypeMap: {
    [mimeType: string]: [StateFactory<any>, string],
  } = {
    'application/hal+json': [halStateFactory, '1.0'],
    'application/vnd.api+json': [jsonApiStateFactory, '0.9'],
    'application/vnd.siren+json': [sirenStateFactory, '0.9'],
    'application/vnd.collection+json': [cjStateFactory, '0.9'],
    'application/json': [halStateFactory, '0.8'],
    'text/html': [htmlStateFactory, '0.7'],
  }

  /**
   * The cache for 'State' objects
   */
  cache: StateCache;

  /**
   * The cache for 'Resource' objects. Each unique uri should
   * only ever get 1 associated resource.
   */
  resources: Map<string, Resource>;

  /**
   * Fetcher is a utility object that handles fetch() requests
   * and middlewares.
   */
  fetcher: Fetcher;

  constructor(bookmarkUri: string);

  /**
   * Follows a relationship, based on its reltype. For example, this might be
   * 'alternate', 'item', 'edit' or a custom url-based one.
   *
   * This function can also follow templated uris. You can specify uri
   * variables in the optional variables argument.
   */
  follow<TFollowedResource = any>(rel: string, variables?: LinkVariables): FollowPromiseOne<TFollowedResource>;

  /**
   * Returns a resource by its uri.
   *
   * This function doesn't do any HTTP requests. The uri is optional. If it's
   * not specified, it will return the bookmark resource.
   *
   * If a relative uri is passed, it will be resolved based on the bookmark
   * uri.
   *
   * @example
   * const res = ketting.go('https://example.org/);
   * @example
   * const res = ketting.go<Author>('/users/1');
   * @example
   * const res = ketting.go(); // bookmark
   */
  go<TResource = any>(uri?: string): Resource<TResource>;

  /**
   * Adds a fetch middleware, which will be executed for
   * each fetch() call.
   *
   * If 'origin' is specified, fetch middlewares can be executed
   * only if the host/origin matches.
   */
  use(middleware: FetchMiddleware, origin: string = '*');

  /**
   * Clears the entire state cache
   */
  clearCache();

  /**
   * Transforms a fetch Response to a State object.
   */
  async getStateForResponse(uri: string, response: Response): Promise<State>;

  /**
   * Caches a State object
   *
   * This function will also emit 'update' events to resources, and store all
   * embedded states.
   */
  cacheState(state: State);

}
```

See also:

* [State](State)
* [Resource](Resource)
