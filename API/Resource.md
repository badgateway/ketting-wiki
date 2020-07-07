```typescript
/**
 * A 'resource' represents an endpoint on a server.
 *
 * A resource has a uri, methods that correspond to HTTP methods,
 * and events to subscribe to state changes.
 */
export class Resource<T = any> extends EventEmitter {

  /**
   * URI of the current resource
   */
  uri: string;

  /**
   * Reference to the Client that created the resource
   */
  client: Client;

  /**
   * Create the resource.
   *
   * This is usually done by the Client.
   */
  constructor(client: Client, uri: string); 

  /**
   * Gets the current state of the resource.
   *
   * This function will return a State object.
   */
  get(getOptions?: GetRequestOptions): Promise<State<T>>; 

  /**
   * Does a HEAD request and returns a HeadState object.
   *
   * If there was a valid existing cache for a GET request, it will
   * still return that.
   */
  async head(headOptions?: HeadRequestOptions): Promise<HeadState>; 

  /**
   * Gets the current state of the resource, skipping
   * the cache.
   *
   * This function will return a State object.
   */
  async refresh(getOptions?: GetRequestOptions): Promise<State<T>>; 

  /**
   * Updates the server state with a PUT request
   */
  async put(options: PutRequestOptions<T> | State): Promise<void>; 

  /**
   * Deletes the resource
   */
  async delete(): Promise<void>; 

  /**
   * Sends a POST request to the resource.
   *
   * See the documentation for PostRequestOptions for more details.
   * This function is used for RPC-like endpoints and form submissions.
   *
   * This function will return the response as a State object.
   */
  async post(options: PostRequestOptions): Promise<State>; 

  /**
   * Sends a POST request, and follows to the next resource.
   *
   * If a server responds with a 201 Status code and a Location header,
   * it will automatically return the newly created resource.
   *
   * If the server responded with a 204 or 205, this function will return
   * `this`.
   */
  async postFollow(options: PostRequestOptions): Promise<Resource>; 

  /**
   * Sends a PATCH request to the resource.
   *
   * This function defaults to a application/json content-type header.
   */
  async patch(options: PatchRequestOptions): Promise<void>; 

  /**
   * Follows a relationship, based on its reltype. For example, this might be
   * 'alternate', 'item', 'edit' or a custom url-based one.
   *
   * This function can also follow templated uris. You can specify uri
   * variables in the optional variables argument.
   */
  follow<TFollowedResource = any>(rel: string, variables?: LinkVariables): FollowPromiseOne<TFollowedResource>; 

  /**
   * Follows a relationship based on its reltype. This function returns a
   * Promise that resolves to an array of Resource objects.
   *
   * If no resources were found, the array will be empty.
   */
  followAll<TFollowedResource = any>(rel: string): FollowPromiseMany<TFollowedResource>; 

  /**
   * Resolves a new resource based on a relative uri.
   *
   * Use this function to manually get a Resource object via a uri. The uri
   * will be resolved based on the uri of the current resource.
   *
   * This function doesn't do any HTTP requests.
   */
  go<TGoResource = any>(uri: string): Resource<TGoResource>; 

  /**
   * Does a HTTP request on the current resource URI
   */
  fetch(init?: RequestInit): Promise<Response>; 

  /**
   * Does a HTTP request on the current resource URI.
   *
   * If the response was a 4XX or 5XX, this function will throw
   * an exception.
   */
  fetchOrThrow(init?: RequestInit): Promise<Response>; 

  /**
   * Updates the state cache, and emits events.
   *
   * This will update the local state but *not* update the server
   */
  updateCache(state: State<T>); 

  /**
   * Clears the state cache for this resource.
   */
  clearCache(): void; 

  /**
   * Returns a Link object, by its REL.
   *
   * If the link does not exist, a LinkNotFound error will be thrown.
   *
   * @deprecated
   */
  async link(rel: string): Promise<Link>; 

  /**
   * Returns all links defined on this object.
   *
   * @deprecated
   */
  async links(rel?: string): Promise<Link[]>; 

  /**
   *
   * Returns true or false depending on if a link with the specified relation
   * type exists.
   *
   * @deprecated
   */
  async hasLink(rel: string): Promise<boolean>; 

  /**
   * Subscribe to the 'update' event.
   *
   * This event will get triggered whenever a new State is received
   * from the server, either through a GET request or if it was
   * transcluded.
   *
   * It will also trigger when calling 'PUT' with a full state object,
   * and when updateCache() was used.
   */
  on(event: 'update', listener: (state: State) => void) : this
  
  /**
   * Subscribe to the 'stale' event.
   *
   * This event will get triggered whenever an unsafe method was
   * used, such as POST, PUT, PATCH, etc.
   *
   * When any of these methods are used, the local cache is stale.
   */
  on(event: 'stale',  listener: () => void) : this;

  /**
   * Subscribe to the 'delete' event.
   *
   * This event gets triggered when the `DELETE` http method is used.
   */
  on(event: 'delete', listener: () => void) : this;

  /**
   * Subscribe to an event and unsubscribe after it was emitted the first time.
   */
  once(event: 'update', listener: (state: State) => void) : this
  once(event: 'stale',  listener: () => void) : this;
  once(event: 'delete', listener: () => void) : this;

  /**
   * Unsubscribe from an event.
   */
  off(event: 'update', listener: (state: State) => void) : this
  off(event: 'stale',  listener: () => void) : this;
  off(event: 'delete', listener: () => void) : this;

  /**
   * Emit an event.
   */
  emit(event: 'update', state: State) : boolean
  emit(event: 'stale') : boolean;
  emit(event: 'delete') : boolean;

}
```

* [State](State)
* [Links](Links)
* [Client](Client)
