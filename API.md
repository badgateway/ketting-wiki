This document has the pulic Ketting API. These are all the types methods you'll
likely need, unless you are extending Ketting.

Methods and properties that are considered 'internal' have been removed from
these types. Feel free to use these methods, they are just less likely to be
useful and more likely to change in new major versions.

TOC
---

{:toc:}

Ketting class
-------------

```typescript
/**
 * The main Ketting client object.
 *
 * This is the starting point for working with Ketting.
 */
class Ketting {

  /**
   * The url from which all discovery starts.
   */
  bookMark: string;

  /**
   * Here we store all the resources that were ever requested. This will
   * ensure that if the same resource is requested twice, the same object is
   * returned.
   */
  resourceCache: { [url: string]: Resource };

  /**
   * Content-Type settings and mappings.
   */
  contentTypes: ContentType[];

  constructor(bookMark: string, options?: Partial<KettingInit>); 

  /**
   * This function is a shortcut for go().follow(x);
   */
  follow<TResource = any>(rel: string, variables?: LinkVariables): Follower<TResource>;

  /**
   * Returns a resource by its uri.
   *
   * This function doesn't do any HTTP requests. The uri is optional. If it's
   * not specified, it will return the bookmark resource.
   *
   * If a relative uri is passed, it will be resolved based on the bookmark
   * uri.
   */
  go<TResource = any>(uri?: string): Resource<TResource>;

  /**
   * This function does an arbitrary request using the fetch API.
   *
   * @see {@link https://developer.mozilla.org/en-US/docs/Web/API/GlobalFetch}
   */
  fetch(input: string|Request, init?: RequestInit): Promise<Response>;

}
```

KettingInit
-----------

Options passed to the constructor. Check out the [Authentication](authentication)
docs for details on the 'auth' property.

```typescript
type KettingInit = {

  /**
   * Authentication options.
   */
  auth?: AuthOptions

  /**
   * A list of settings passed to the Fetch API.
   *
   * It's effectively a list of defaults that are passed as the 'init' argument.
   * @see https://developer.mozilla.org/en-US/docs/Web/API/Request/Request
   */
  fetchInit: RequestInit,

  /**
   * Per-domain options.
   *
   * This setting allows you to override specific options on a per-domain
   * basis. It's possible to specify wildcards here.
   */
  match: {
    [domain: string]: {
      auth?: AuthOptions
      fetchInit?: RequestInit,
    }
  }
};
```


Resource class
--------------

```typescript
/**
 * A 'resource' represents an endpoint on the server.
 *
 * The endpoint has a uri, you might for example be able to GET its
 * presentation.
 *
 * A resource may also have a list of links on them, pointing to other
 * resources.
 */
class Resource<TResource = any, TPatch = Partial<TResource>> {

  /**
   * Reference to the main Client
   */
  client: Ketting;

  /**
   * The uri of the resource
   */
  uri: string;

  /**
   * A default mimetype for the resource.
   *
   * This mimetype is used for PUT and POST requests by default.
   * The mimetype is sniffed in a few different ways.
   *
   * If a GET request is done, and the GET request had a mimetype it will
   * be used to set this value.
   *
   * It's also possible for resources to get a mimetype through a link.
   *
   * If the mimetype was "null" when doing the request, the chosen mimetype
   * will come from the first item in Client.resourceTypes
   */
  contentType: string | null;

  /**
   * Fetches the resource representation.
   * Returns a promise that resolves to a parsed json object.
   */
  get(): Promise<TResource>;

  /**
   * Updates the resource representation with a new JSON object.
   */
  put(body: TResource): Promise<void>; 

  /**
   * Updates the resource representation with a new JSON object.
   */
  delete(): Promise<void>; 

  /**
   * Sends a POST request to the resource.
   *
   * This function assumes that POST is used to create new resources, and
   * that the response will be a 201 Created along with a Location header that
   * identifies the new resource location.
   *
   * This function returns a Promise that resolves into the newly created
   * Resource.
   *
   * If no Location header was given, it will resolve still, but with an empty
   * value.
   */
  post<TPostResource = any>(body: TPostResource): Promise<Resource<TPostResource>|null>;

  /**
   * Sends a PATCH request to the resource.
   *
   * This function defaults to a application/json content-type header.
   */
  patch(body: TPatch): Promise<void>;

  /**
   * Refreshes the representation for this resource.
   *
   * This function will return the a parsed JSON object, like the get
   * function does.
   */
  refresh(): Promise<TResource>;

  /**
   * Returns the links for this resource, as a promise.
   *
   * The rel argument is optional. If it's given, we will only return links
   * from that relationship type.
   */
  links(rel?: string): Promise<Link[]>; 

  /**
   * Returns a specific link based on it's rel.
   *
   * If multiple links with the same rel existed, we're only returning the
   * first. If no link with the specified link existed, a LinkNotFound
   * exception will be thrown.
   *
   * The rel argument is optional. If it's given, we will only return links
   * from that relationship type.
   */
  link(rel: string): Promise<Link>;

  /**
   * Follows a relationship, based on its reltype. For example, this might be
   * 'alternate', 'item', 'edit' or a custom url-based one.
   *
   * This function can also follow templated uris. You can specify uri
   * variables in the optional variables argument.
   */
  follow<TFollowedResource = any>(rel: string, variables?: LinkVariables): Follower<TFollowedResource>;

  /**
   * Follows a relationship based on its reltype. This function returns a
   * Promise that resolves to an array of Resource objects.
   *
   * If no resources were found, the array will be empty.
   */
  followAll<TFollowedResource = any>(rel: string): Promise<Array<Resource<TFollowedResource>>>;

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
   * Returns the representation for the object.
   * If it wasn't fetched yet, this function does the fetch as well.
   *
   * Usually you will want to use the `get()` method instead, unless you need
   * the full object.
   */
  representation(): Promise<Representator<TResource>>;

  /**
   * Clears the internal representation cache.
   */
  clearCache(): void;

  /**
   * Does an arbitrary HTTP request on the resource using the Fetch API.
   *
   * The method signature is the same as the MDN fetch object. However, it's
   * possible in this case to not specify a URI or specify a relative URI.
   *
   * When doing the actual request, any relative uri will be resolved to the
   * uri of the current resource.
   *
   * @see https://developer.mozilla.org/en-US/docs/Web/API/Request/Request
   */
  fetch(input: Request|string|RequestInit, init?: RequestInit): Promise<Response>;

  /**
   * Does a HTTP request and throws an exception if the server emitted
   * a HTTP error.
   *
   * @see https://developer.mozilla.org/en-US/docs/Web/API/Request/Request
   */
  fetchAndThrow(input: Request|string|RequestInit, init?: RequestInit): Promise<Response>;

}
```

Link class
----------

```typescript
/**
 * The Link object represents a hyperlink.
 */
export class Link {

  /**
   * The base href of the parent document. Used for expanding relative links.
   */
  context: string;

  /**
   * The URI of the link. Might be relative
   */
  href: string;

  /**
   * The name for a link. This might be used to disambiguate the link.
   *
   * If you're looking at this, chances are that you might want 'title'
   * instead.
   */
  name?: string;

  /**
   * The relationship type
   */
  rel: string;

  /**
   * Is it a URI template or not?
   */
  templated: boolean;

  /**
   * A human-readable label for the link.
   */
  title: string | null;

  /**
   * A mimetype
   */
  type: string | null;

  /**
   * Returns the absolute link url, based on it's base and relative url.
   */
  resolve(): string; 

  /**
   * Expands a link template (RFC6570) and resolves the uri
   *
   * @param {object} variables - A list of variables to expand the link with.
   * @returns {string}
   */
  expand(variables: object): string;
  
}
```

Follower
--------

```typescript
/**
 * The Follower class is what's being returned from follow() functions.
 *
 * It's 'PromiseLike', which means you can treat it like a Promise, and it
 * can be awaited. When used as a Promise, it resolves to the Resource object
 * that was followed.
 *
 * In addition to being a Promise<Resource> stand-in, it also exposes other
 * functions, namely:
 *
 * * `follow()` to allow a user to chain several follow() functions to do
 *   several 'hops' all at once.
 * * `followAll()`, allowing a user to call `followAll()` at the end of a
 *   chain.
 */
class Follower<T = any> implements PromiseLike<Resource<T>> {

  /**
   * This 'then' function behaves like a Promise then() function.
   *
   * This method signature is pretty crazy, but trust that it's pretty much
   * like any then() method on a promise.
   */
  then<TResult1 = Resource<T>, TResult2 = never>(
    onfulfilled?: ((value: Resource<T>) => TResult1 | PromiseLike<TResult1>) | null | undefined,
    onrejected?: ((reason: Error) => TResult2 | PromiseLike<TResult2>) | null | undefined
  ): Promise<TResult1 | TResult2>; 

  /**
   * This 'then' function behaves like a Promise then() function.
   */
  catch<TResult1 = any, TResult2 = never>(onrejected?: ((reason: Error) => TResult2 | PromiseLike<TResult2>) | null | undefined): Promise<TResult1 | TResult2>;

  /**
   * Follow another link immediately after following this link.
   *
   * This allows you to follow several hops of links in one go.
   *
   * For example: resource.follow('foo').follow('bar');
   */
  follow<TNested = any>(rel: string, variables?: LinkVariables): Follower<TNested>; 

  /**
   * Follows a set of links immediately after following this link.
   *
   * For example: resource.follow('foo').followAll('item');
   */
  followAll<TNested = any>(rel: string): Promise<Array<Resource<TNested>>>; 

}
```

Representator
-------------

You're less likely to need the 'representor' class. It's responsible for
parsing specific formats like HAL, JSON:API, Siren, HTML.

```typescript
/**
 * The Representation class is basically a 'body' of a request
 * or response.
 *
 * This is base class for a representation.
 */
abstract class Representation<T = string> {

  contentType: string;
  uri: string;

  getLink(rel: string): Link;
  getLinks(rel?: string): Link[];
  getEmbedded(): { [uri: string]: T }; 

  /**
   * Returns the parsed body for this representation.
   *
   * Specific implementations of this class might alter the response before
   * returning, for example to remove meta-information that's not relevant
   * the user of this object.
   */
  getBody(): T; 

  setBody(body: T);

}
```
