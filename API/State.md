```typescript
interface State<T> {

  /**
   * The URI associated with this state
   */
  uri: string;

  /**
   * Represents the body of the HTTP response.
   *
   * In the case of a JSON response, this will be deserialized
   */
  data: T

  /**
   * The full list of HTTP headers that were sent with the response.
   */
  headers: Headers;

  /**
   * All links associated with the resource.
   */
  links: Links;

  /**
   * Reference to main client that created this state
   */
  client: Client;

  /**
   * Content-headers are a subset of HTTP headers that related directly
   * to the content. The obvious ones are Content-Type.
   *
   * This set of headers will be sent by the server along with a GET
   * response, but will also be sent back to the server in a PUT
   * request.
   */
  contentHeaders(): Headers;

  /**
   * Return an action by name.
   *
   * If the format provides a default action, the name may be omitted.
   */
  action<TFormData = any>(name?: string): Action<TFormData>;

  /**
   * Returns a serialization of the state that can be used in a HTTP
   * response.
   *
   * For example, a JSON object might simply serialize using
   * JSON.serialize().
   */
  serializeBody(): Buffer|Blob|string;

  /**
   * Certain formats can embed other resources, identified by their
   * own URI.
   *
   * When a format has embedded resources, we will use these to warm
   * the cache.
   *
   * This method returns every embedded resource.
   */
  getEmbedded(): State[];

  /**
   * Timestamp of when the State was first generated
   */
  timestamp: number;

  /**
   * Deep-copies this State object.
   */
  clone(): State<T>;

}
```

* [State](State)
* [Links](Links)
* [Action](Action)
