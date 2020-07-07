[ketting](../README.md) › [Globals](../globals.md) › ["src/cache/forever"](../modules/_src_cache_forever_.md) › [ForeverCache](_src_cache_forever_.forevercache.md)

# Class: ForeverCache

The 'Forever' cache stores any State for as long as the application
lives.

It is a good default for most applications, but it means that if
a resource was changed server-side, Ketting will not pick up that change
until something was done to expire caches.

Executing an unsafe method, calling clearCache() on a resource, or
when a resource appears in Location, Content-Location, or "invalidates"
link relationships.

## Hierarchy

* **ForeverCache**

  ↳ [ShortCache](_src_cache_short_.shortcache.md)

## Implements

* [StateCache](../interfaces/_src_cache_index_.statecache.md)

## Index

### Constructors

* [constructor](_src_cache_forever_.forevercache.md#constructor)

### Properties

* [cache](_src_cache_forever_.forevercache.md#private-cache)

### Methods

* [clear](_src_cache_forever_.forevercache.md#clear)
* [delete](_src_cache_forever_.forevercache.md#delete)
* [get](_src_cache_forever_.forevercache.md#get)
* [has](_src_cache_forever_.forevercache.md#has)
* [store](_src_cache_forever_.forevercache.md#store)

## Constructors

###  constructor

\+ **new ForeverCache**(): *[ForeverCache](_src_cache_forever_.forevercache.md)*

*Defined in [src/cache/forever.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L18)*

**Returns:** *[ForeverCache](_src_cache_forever_.forevercache.md)*

## Properties

### `Private` cache

• **cache**: *Map‹string, [State](../interfaces/_src_state_interface_.state.md)›*

*Defined in [src/cache/forever.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L18)*

## Methods

###  clear

▸ **clear**(): *void*

*Defined in [src/cache/forever.ts:68](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L68)*

Purge the entire cache

**Returns:** *void*

___

###  delete

▸ **delete**(`uri`: string): *void*

*Defined in [src/cache/forever.ts:61](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L61)*

Delete a State object from the cache, by its uri

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *void*

___

###  get

▸ **get**(`uri`: string): *[State](../interfaces/_src_state_interface_.state.md) | null*

*Defined in [src/cache/forever.ts:39](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L39)*

Retrieve a State object from the cache by its absolute uri

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *[State](../interfaces/_src_state_interface_.state.md) | null*

___

###  has

▸ **has**(`uri`: string): *boolean*

*Defined in [src/cache/forever.ts:52](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L52)*

Return true if a State object with the specified uri exists in the cache

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *boolean*

___

###  store

▸ **store**(`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

*Defined in [src/cache/forever.ts:29](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L29)*

Store a State object.

This function will clone the state object before storing

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *void*
