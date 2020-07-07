[ketting](../README.md) › [Globals](../globals.md) › ["src/cache/never"](../modules/_src_cache_never_.md) › [NeverCache](_src_cache_never_.nevercache.md)

# Class: NeverCache

The NeverCache caches absolutely nothing.

This should usually only be used in testing scenarios or if you really
know what you're doing.

Using it could cause excessive requests, and will cause embedded items
to be ignored.

## Hierarchy

* **NeverCache**

## Implements

* [StateCache](../interfaces/_src_cache_index_.statecache.md)

## Index

### Methods

* [clear](_src_cache_never_.nevercache.md#clear)
* [delete](_src_cache_never_.nevercache.md#delete)
* [get](_src_cache_never_.nevercache.md#get)
* [has](_src_cache_never_.nevercache.md#has)
* [store](_src_cache_never_.nevercache.md#store)

## Methods

###  clear

▸ **clear**(): *void*

*Defined in [src/cache/never.ts:50](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/never.ts#L50)*

Purge the entire cache

**Returns:** *void*

___

###  delete

▸ **delete**(`uri`: string): *void*

*Defined in [src/cache/never.ts:43](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/never.ts#L43)*

Delete a State object from the cache, by its uri

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *void*

___

###  get

▸ **get**(`uri`: string): *null*

*Defined in [src/cache/never.ts:27](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/never.ts#L27)*

Retrieve a State object from the cache by its absolute uri

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *null*

___

###  has

▸ **has**(`uri`: string): *boolean*

*Defined in [src/cache/never.ts:34](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/never.ts#L34)*

Return true if a State object with the specified uri exists in the cache

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *boolean*

___

###  store

▸ **store**(`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

*Defined in [src/cache/never.ts:20](https://github.com/evert/ketting/blob/f7a0a1b/src/cache/never.ts#L20)*

Store a State object.

This function will clone the state object before storing

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *void*
