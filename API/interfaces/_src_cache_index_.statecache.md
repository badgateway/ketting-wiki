[ketting](../README.md) › [Globals](../globals.md) › ["src/cache/index"](../modules/_src_cache_index_.md) › [StateCache](_src_cache_index_.statecache.md)

# Interface: StateCache

Cache interface

The cache is responsible for storing 'state' objects

## Hierarchy

* **StateCache**

## Implemented by

* [ForeverCache](../classes/_src_cache_forever_.forevercache.md)
* [NeverCache](../classes/_src_cache_never_.nevercache.md)
* [ShortCache](../classes/_src_cache_short_.shortcache.md)

## Index

### Properties

* [clear](_src_cache_index_.statecache.md#clear)
* [delete](_src_cache_index_.statecache.md#delete)
* [get](_src_cache_index_.statecache.md#get)
* [has](_src_cache_index_.statecache.md#has)
* [store](_src_cache_index_.statecache.md#store)

## Properties

###  clear

• **clear**: *function*

*Defined in [src/cache/index.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/index.ts#L38)*

Purge the entire cache

#### Type declaration:

▸ (): *void*

___

###  delete

• **delete**: *function*

*Defined in [src/cache/index.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/index.ts#L33)*

Delete a State object from the cache, by its uri

#### Type declaration:

▸ (`uri`: string): *void*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

___

###  get

• **get**: *function*

*Defined in [src/cache/index.ts:23](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/index.ts#L23)*

Retrieve a State object from the cache by its absolute uri

#### Type declaration:

▸ (`uri`: string): *[State](_src_state_interface_.state.md) | null*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

___

###  has

• **has**: *function*

*Defined in [src/cache/index.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/index.ts#L28)*

Return true if a State object with the specified uri exists in the cache

#### Type declaration:

▸ (`uri`: string): *boolean*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

___

###  store

• **store**: *function*

*Defined in [src/cache/index.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/index.ts#L18)*

Store a State object.

This function will clone the state object before storing

#### Type declaration:

▸ (`state`: [State](_src_state_interface_.state.md)): *void*

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](_src_state_interface_.state.md) |
