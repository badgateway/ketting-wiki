*Note: it's strongly advisable to read [Getting Started](Getting-Started),
first as this page builds upon all the established concepts there.*

If your REST API uses Hypermedia in any way, Ketting gets additional
powers. Ketting allows you to traverse your API through links that
it exposes and discover endpoints and features.

For your links to be recognized, they need to either appear in
[HTTP Link Headers][weblinking], or your API needs to generate one
of the following Hypermedia formats:

* [Hal][hal]
* [Siren][siren]
* [JSON:API][jsonapi]
* [Collection+JSON][cj]
* Or HTML! It can pick up links from [`<a>`][html-a] or [`<link>`][html-link]
  tags, as long as they have a have a `rel` and a `href` attribute.

Lets start with a simple example. Our API has an 'article'. Articles
may have authors. If you're using HAL, your server might emit something
like this (note: slightly simplified).

```json
{
  "_links": {
    "author": { "href": "/authors/123", "title": "Dr. Pidgin" }
  },
  "title": "Hello world!",
  "body": "..."
}
```

Let's get access to this resource:

```typescript
import { Client } from 'ketting';

const client = new Client('https://api.example');
const articleRes = client.go('/acticle/1');
```

Now we have an 'article' resource, we want to find the related `author`
resource. We do this what's called the "rel" or "relationship type".

```typescript
const authorRes = await articleRes.follow('author');
```

That's it. `authorRes` is a new Resource object that refers to
`https://api.example/authors/123`.


A more complex example
----------------------

Lets do a more complex example. Our API has a home document that has
a list of links with resources available on the server.

One of those is an `article-collection`. The `article-collection` has
a list of every article in the API. Each article is listed in the collection
as an `item` link.

HAL example of the home document:

```json
{
  "_links": {
    "author-collection": { "href": "/authors", "title": "List of authors" },
    "article-collection": { "href": "/articles", "title": "List of articles" },
    "help": { "href": "mailto:support@api.example" }
  },
  "motd": "Welcome to the blogging server!"
}
```

HAL example of the article collection:

```json
{
  "_links": {
    "item": [
      { "href": "/articles/1" },
      { "href": "/articles/2" },
      { "href": "/articles/3" }
    ],
    "next": { "href": "/articles?page=2" }
  },
  "total": 25
}
```

Our goal is now to get a full list of articles, and log their bodies.

```typescript
const client = new Client('https://api.example/');

// If the argument to 'go' is omitted, we go to the bookmark url or
// home document.
const home = client.go();

// Find the article collection
const articleCollection = await home.follow('article-collection');

// 'followAll' returns an array of resources
const articleResources = await articleCollection.followAll('item');

for(const resource of articleResources) {
  const state = await resource.get();
  console.log(state.data);
}
```

At this point you might ask: Is doing a lot of sequential `GET` request
going to be slow? The answer is: yes it might, but there are a number of
optimization strategies that Ketting supports, including prefetching,
paralizing, embedding/compound resources and leveraging HTTP/2 Push.

Read [Optimizing](Optimizing) for more details about this topic.

Chaining hops
-------------

If you need to do several steps of `.follow()` and/or `.followAll()`, you can
just chain them together:

```typescript
// Lets find the author of the first article

const client = new Client('https://api.example/');
const home = client.go();

const author = await home
  .follow('article-collection')
  .follow('item') // If there's more than 1, it will return the first
  .follow('author');
```

Mixing formats
--------------

In the last example, we did 3 hops. Any of those can be any of the
supported Hypermedia formats.

This means that the 'home document' could have been written in HTML:

```html
<ul>
  <li><a href="/articles" rel="article-collection">List of articles</a></li>
  <li><a href="/authors" rel="author-collection">List of authors</a></li>
</ul>
```

If the home document _was_ written in HTML, everything would still have worked
the same.

Perhaps you want to link to another Hypermedia API that also uses links, but
a different format. Ketting abstracts this away, and all you need to kow as a
user is that they use one of the supported hypermedia formats.

State and links
---------------

When you retrieve a state using the `.get()` function, in most formats links
will be stripped.

If we go back to our earlier HAL example:

```json
{
  "_links": {
    "author": { "href": "/authors/123", "title": "Dr. Pidgin" }
  },
  "title": "Hello world!",
  "body": "..."
}
```

Then if we log the data we only get the `title` and `body` properties:

```typescript
const state = await authorRes.get();
console.log(state.data); // Show the title and body, but not _links
```

To get access to the links, you can use `state.links`.

`state.links` is a `Links` class that provides a simple way to interact with
a set of links, and abstracts all the different formats.

Now our goal is to add a category to an article. We do this via a link:

```typescript
const state = await authorRes.get();
state.links.add({
  href: '/category/5,
  rel: 'category'
});
await authorRes.put(state);
```

The `.put()` function will re-serialize the object and the PUT request
body will look something like this:

```json
{
  "_links": {
    "author": { "href": "/authors/123", "title": "Dr. Pidgin" },
    "category": { "href": "/category/5" }
  },
  "title": "Hello world!",
  "body": "..."
}
```

The `state.links` object also has functions for getting information about
links and multiple ways to mutate the list. See the [Links](Links) API
documentation for details.

Actions
-------

TODO: Section needs more work.

Some hypermedia formats have support for 'actions'. This could be a
[Siren][siren] action, but HTML forms are also supported.

Not every Hypermedia API uses these actions, but if they do, you can
execute an action via the state object.

```typescript
const state = await authorRes.get();
await state
  .action('send-message')
  .submit({ body: "HI!" });
```

As before, this feature works regardless of the underlying format.

Templated links
---------------

Some formats define templated links. Here's a HAL example of our
article collection, with a `search` templated link:

```json
{
  "_links": {
    "item": [
      { "href": "/articles/1" },
      { "href": "/articles/2" },
      { "href": "/articles/3" }
    ],
    "search": {
      "templated": true,
      "href": "/articles{?q}"
    },
    "next": { "href": "/articles?page=2" }
  },
  "total": 25
}
```

To follow a templated link, use the second argument of `.follow()`

```typescript
// Search for articles that mention 'javascript'
const result = articleCollection
  .follow('search', {q: 'Javascript'});
```

Next steps
----------

* [Optimizing many requests](Optimizing).
* [Typescript features](Typescript-Features).

[weblinking]: https://tools.ietf.org/html/rfc8288
[html-a]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a
[html-link]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link
[hal]: https://tools.ietf.org/html/draft-kelly-json-hal-00
[siren]: https://github.com/kevinswiber/siren
[jsonapi]: https://jsonapi.org/
[weblinking]: https://tools.ietf.org/html/rfc8288
[cj]: http://amundsen.com/media-types/collection/
