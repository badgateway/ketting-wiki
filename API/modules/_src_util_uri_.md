[ketting](../README.md) › [Globals](../globals.md) › ["src/util/uri"](_src_util_uri_.md)

# Module: "src/util/uri"

## Index

### Type aliases

* [UrlParts](_src_util_uri_.md#urlparts)

### Functions

* [parse](_src_util_uri_.md#parse)
* [resolve](_src_util_uri_.md#resolve)

## Type aliases

###  UrlParts

Ƭ **UrlParts**: *object*

*Defined in [src/util/uri.ts:4](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.ts#L4)*

#### Type declaration:

* **host**? : *undefined | string*

## Functions

###  parse

▸ **parse**(`url`: string): *[UrlParts](_src_util_uri_.md#urlparts)*

*Defined in [src/util/uri.ts:30](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.ts#L30)*

Parses a url in multiple components.

This is the node.js version.

**Parameters:**

Name | Type |
------ | ------ |
`url` | string |

**Returns:** *[UrlParts](_src_util_uri_.md#urlparts)*

___

###  resolve

▸ **resolve**(`base`: string, `relative`: string): *string*

*Defined in [src/util/uri.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.ts#L13)*

Resolves a relative url using another url.

This is the node.js version.

**Parameters:**

Name | Type |
------ | ------ |
`base` | string |
`relative` | string |

**Returns:** *string*

▸ **resolve**(`link`: [Link](_src_link_.md#link)): *string*

*Defined in [src/util/uri.ts:14](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.ts#L14)*

**Parameters:**

Name | Type |
------ | ------ |
`link` | [Link](_src_link_.md#link) |

**Returns:** *string*
