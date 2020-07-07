[ketting](../README.md) › [Globals](../globals.md) › ["src/link"](../modules/_src_link_.md) › [Links](_src_link_.links.md)

# Class: Links

Links container, providing an easy way to manage a set of links.

## Hierarchy

* **Links**

## Index

### Constructors

* [constructor](_src_link_.links.md#constructor)

### Properties

* [defaultContext](_src_link_.links.md#defaultcontext)
* [store](_src_link_.links.md#store)

### Methods

* [add](_src_link_.links.md#add)
* [delete](_src_link_.links.md#delete)
* [get](_src_link_.links.md#get)
* [getAll](_src_link_.links.md#getall)
* [getMany](_src_link_.links.md#getmany)
* [has](_src_link_.links.md#has)
* [set](_src_link_.links.md#set)

## Constructors

###  constructor

\+ **new Links**(`defaultContext`: string, `links?`: [Link](../modules/_src_link_.md#link)[] | [Links](_src_link_.links.md)): *[Links](_src_link_.links.md)*

*Defined in [src/link.ts:62](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L62)*

**Parameters:**

Name | Type |
------ | ------ |
`defaultContext` | string |
`links?` | [Link](../modules/_src_link_.md#link)[] &#124; [Links](_src_link_.links.md) |

**Returns:** *[Links](_src_link_.links.md)*

## Properties

###  defaultContext

• **defaultContext**: *string*

*Defined in [src/link.ts:64](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L64)*

___

###  store

• **store**: *Map‹string, [Link](../modules/_src_link_.md#link)[]›*

*Defined in [src/link.ts:62](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L62)*

## Methods

###  add

▸ **add**(...`links`: object | object[]): *void*

*Defined in [src/link.ts:83](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L83)*

Adds a link to the list

**Parameters:**

Name | Type |
------ | ------ |
`...links` | object &#124; object[] |

**Returns:** *void*

▸ **add**(`rel`: string, `href`: string): *void*

*Defined in [src/link.ts:84](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L84)*

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |
`href` | string |

**Returns:** *void*

___

###  delete

▸ **delete**(`rel`: string): *void*

*Defined in [src/link.ts:145](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L145)*

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *void*

___

###  get

▸ **get**(`rel`: string): *[Link](../modules/_src_link_.md#link) | undefined*

*Defined in [src/link.ts:135](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L135)*

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *[Link](../modules/_src_link_.md#link) | undefined*

___

###  getAll

▸ **getAll**(): *[Link](../modules/_src_link_.md#link)[]*

*Defined in [src/link.ts:157](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L157)*

**Returns:** *[Link](../modules/_src_link_.md#link)[]*

___

###  getMany

▸ **getMany**(`rel`: string): *[Link](../modules/_src_link_.md#link)[]*

*Defined in [src/link.ts:151](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L151)*

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *[Link](../modules/_src_link_.md#link)[]*

___

###  has

▸ **has**(`rel`: string): *boolean*

*Defined in [src/link.ts:165](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L165)*

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *boolean*

___

###  set

▸ **set**(`link`: [Link](../modules/_src_link_.md#link) | [NewLink](../modules/_src_link_.md#newlink)): *void*

*Defined in [src/link.ts:114](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L114)*

Set a link

If a link with the provided 'rel' already existed, it will be overwritten.

**Parameters:**

Name | Type |
------ | ------ |
`link` | [Link](../modules/_src_link_.md#link) &#124; [NewLink](../modules/_src_link_.md#newlink) |

**Returns:** *void*

▸ **set**(`rel`: string, `href`: string): *void*

*Defined in [src/link.ts:115](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L115)*

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |
`href` | string |

**Returns:** *void*
