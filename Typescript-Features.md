Ketting has a number of features making it possible to add stricter typing
to resources. It does this with generics.

By default, when you obtain a resource with `follow()`, you will get an object
with type `Resource<any>`.

```typescript
// authorRes is Resource<any>
const authorRes = await someRes.follow('item');
```

This causes the signatures of `put()` and `get()` to rougly look like this:

```typescript
class Resource {
  get(): Promise<any>;
  put(body: any): Promise<void>
}
```

If you know what the shape of the object is that you're receiving via `GET`,
you can specify this on the relevant `follow()` function:

```typescript
type Author = {
  firstName: string,
  lastName: string,
};

// Will have type Resource<Author>
const authorRes = await someRes.follow<Author>('item');

// Will have type Author
const author = await author.get();
```

The `get` and `put` signatures now look like this:

```typescript
class Resource {
  get(): Promise<Author>;
  put(body: Author): Promise<void>
}
```

This same feature also exists on other functions that return resources.

```typescript
// Returns Resource<Author>[] 
const resources = await resource.followAll<Author>('item');

// Returns Resource<Author>
const resource = await recource.go<Author>('?relative-link');
```

When a Resource is typed, it also assumes that the type for the `patch()`
method is `Partial<Author>`, meaning that the assumption is that the HTTP
Patch method takes a a JSON object that's a subset of 'Author'.

Not every API will take that approach with PATCH, so it's also possible to
override the type for patch.

```typescript
const res:Resource<Author, SomeFancyPatchFormat> = await otherRes.follow('...');
```

Lastly, if your API creates new resources with `POST`, and the server returns
`201 Created` and a `Location` header, the `post()` function returns a resource
of the same type.

```typescript
const authorCollection = await res.follow('author-collection');

const newAuthor:Author = {
  firstName: 'Ursula',
  lastName: 'Le Guin',
};

const newAuthorResource = await authorCollection.post(newAuthor);
// newAuthorResource will now be typed as Resource<Author>
```

tl;dr
-----

These are the most relevant methods from the Resource type:

```typescript
class Resource<TResource = any, TPatch = Partial<TResource>> {

  get(): Promise<TResource>;
  put(body: TResource): Promise<void> {
  delete(): Promise<void>; 

  post<TPostResource = any>(body: TPostResource): Promise<Resource<TPostResource>|null>;
  patch(body: TPatch): Promise<void>; 

  refresh(): Promise<TResource>;

  follow<TFollowedResource = any>(rel: string, variables?: LinkVariables): Follower<TFollowedResource>; 
  followAll<TFollowedResource = any>(rel: string): Promise<Array<Resource<TFollowedResource>>>;

  go<TGoResource = any>(uri: string): Resource<TGoResource>; 

}
```
