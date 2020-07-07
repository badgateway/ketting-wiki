```typescript
export type Link = {
  /**
   * Target URI
   */
  href: string,

  /**
   * Context URI.
   *
   * Used to resolve relative URIs
   */
  context: string;

  /**
   * Relation type
   */
  rel: string,

  /**
   * Link title
   */
  title?: string,

  /**
   * Content type hint of the target resource
   */
  type?: string,

  /**
   * Anchor.
   *
   * This describes where the link is linked from, from for example
   * a fragment in the current document
   */
  anchor?: string,

  /**
   * Language of the target resource
   */
  hreflang?: string,

  /**
   * HTML5 media attribute
   */
  media?: string,

  /**
   * If templated is set to true, the href is a templated URI.
   */
  templated?: boolean,

}
```

```typescript
/**
 * Links container, providing an easy way to manage a set of links.
 */
class Links {

  constructor(public defaultContext: string, links?: Link[] | Links);

  /**
   * Adds a link to the list
   */
  add(...links: (Link | NewLink)[]): void
  add(rel: string, href: string): void

  /**
   * Set a link
   *
   * If a link with the provided 'rel' already exists, it will be overwritten.
   */
  set(link: Link | NewLink): void
  set(rel: string, href: string): void

  /**
   * Return a single link by its 'rel'.
   *
   * If the link does not exist, undefined is returned.
   */
  get(rel: string): Link|undefined;

  /**
   * Delete all links with the given 'rel'.
   */
  delete(rel: string): void;

  /**
   * Return all links that have a given rel.
   *
   * If no links with the rel were found, an empty array is returned.
   */
  getMany(rel: string): Link[];

  /**
   * Return all links.
   */
  getAll(): Link[];

  /**
   * Returns true if at least 1 link with the given rel exists.
   */
  has(rel: string): boolean;

}
```

```typescript
/**
 * The LinkNotFound error gets thrown whenever something tries to follow a
 * link by its rel, that doesn't exist
 */
class LinkNotFound extends Error {}
```

See also:

* [State](State)
