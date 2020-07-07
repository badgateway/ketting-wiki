[ketting](../README.md) › [Globals](../globals.md) › ["src/cache/short"](../modules/_src_cache_short_.md) › [ShortCache](_src_cache_short_.shortcache.md)

# Class: ShortCache

ShortCache stores items in the cache for a short time.

This cache can be a good choice if your server heavily relies
on HTTP cache headers and Ketting runs in your browser, or if in general
you want very up-to-date data.

The reason in this scenarios it's useful to still have a 'very temporary'
cache, is because during many operations `get()` may be called in rapid
succession, and it also allows for enough time for 'embedded items' to
pe placed in the cache and extracted again.

## Hierarchy

* [ForeverCache](_src_cache_forever_.forevercache.md)

  ↳ **ShortCache**

## Implements

* [StateCache](../interfaces/_src_cache_index_.statecache.md)

## Index

### Constructors

* [constructor](_src_cache_short_.shortcache.md#constructor)

### Properties

* [activeTimers](_src_cache_short_.shortcache.md#private-activetimers)
* [cacheTimeout](_src_cache_short_.shortcache.md#private-cachetimeout)

### Methods

* [clear](_src_cache_short_.shortcache.md#clear)
* [delete](_src_cache_short_.shortcache.md#delete)
* [get](_src_cache_short_.shortcache.md#get)
* [has](_src_cache_short_.shortcache.md#has)
* [setTimer](_src_cache_short_.shortcache.md#private-settimer)
* [store](_src_cache_short_.shortcache.md#store)

## Constructors

###  constructor

\+ **new ShortCache**(`cacheTimeout`: number): *[ShortCache](_src_cache_short_.shortcache.md)*

*Overrides [ForeverCache](_src_cache_forever_.forevercache.md).[constructor](_src_cache_forever_.forevercache.md#constructor)*

*Defined in [src/cache/short.ts:19](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/short.ts#L19)*

Create the short cache.

cacheTimeout is specified in ms.

**Parameters:**

Name | Type | Default |
------ | ------ | ------ |
`cacheTimeout` | number | 30000 |

**Returns:** *[ShortCache](_src_cache_short_.shortcache.md)*

## Properties

### `Private` activeTimers

• **activeTimers**: *Map‹string, ReturnType‹typeof setInterval››*

*Defined in [src/cache/short.ts:19](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/short.ts#L19)*

___

### `Private` cacheTimeout

• **cacheTimeout**: *number*

*Defined in [src/cache/short.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/short.ts#L18)*

## Methods

###  clear

▸ **clear**(): *void*

*Inherited from [ForeverCache](_src_cache_forever_.forevercache.md).[clear](_src_cache_forever_.forevercache.md#clear)*

*Defined in [src/cache/forever.ts:68](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L68)*

Purge the entire cache

**Returns:** *void*

___

###  delete

▸ **delete**(`uri`: string): *void*

*Inherited from [ForeverCache](_src_cache_forever_.forevercache.md).[delete](_src_cache_forever_.forevercache.md#delete)*

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

*Inherited from [ForeverCache](_src_cache_forever_.forevercache.md).[get](_src_cache_forever_.forevercache.md#get)*

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

*Inherited from [ForeverCache](_src_cache_forever_.forevercache.md).[has](_src_cache_forever_.forevercache.md#has)*

*Defined in [src/cache/forever.ts:52](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/forever.ts#L52)*

Return true if a State object with the specified uri exists in the cache

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *boolean*

___

### `Private` setTimer

▸ **setTimer**(`uri`: string): *void*

*Defined in [src/cache/short.ts:42](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/short.ts#L42)*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *void*

___

###  store

▸ **store**(`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

*Overrides [ForeverCache](_src_cache_forever_.forevercache.md).[store](_src_cache_forever_.forevercache.md#store)*

*Defined in [src/cache/short.ts:37](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/short.ts#L37)*

Store a State object.

This function will clone the state object before storing

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *void*
