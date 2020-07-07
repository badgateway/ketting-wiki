[ketting](../README.md) › [Globals](../globals.md) › ["src/util/uri.web"](_src_util_uri_web_.md)

# Module: "src/util/uri.web"

## Index

### Type aliases

* [UrlParts](_src_util_uri_web_.md#urlparts)

### Functions

* [parse](_src_util_uri_web_.md#parse)
* [resolve](_src_util_uri_web_.md#resolve)

## Type aliases

###  UrlParts

Ƭ **UrlParts**: *object*

*Defined in [src/util/uri.web.ts:3](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.web.ts#L3)*

#### Type declaration:

* **host**? : *undefined | string*

## Functions

###  parse

▸ **parse**(`url`: string): *[UrlParts](_src_util_uri_web_.md#urlparts)*

*Defined in [src/util/uri.web.ts:54](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.web.ts#L54)*

Parses a url in multiple components.

This is the browser-based version.

**Parameters:**

Name | Type |
------ | ------ |
`url` | string |

**Returns:** *[UrlParts](_src_util_uri_web_.md#urlparts)*

___

###  resolve

▸ **resolve**(`base`: string, `relative`: string): *string*

*Defined in [src/util/uri.web.ts:12](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.web.ts#L12)*

Resolves a relative url using another url.

This is the browser-based version.

**Parameters:**

Name | Type |
------ | ------ |
`base` | string |
`relative` | string |

**Returns:** *string*

▸ **resolve**(`link`: [Link](_src_link_.md#link)): *string*

*Defined in [src/util/uri.web.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/util/uri.web.ts#L13)*

**Parameters:**

Name | Type |
------ | ------ |
`link` | [Link](_src_link_.md#link) |

**Returns:** *string*
