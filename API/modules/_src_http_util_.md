[ketting](../README.md) › [Globals](../globals.md) › ["src/http/util"](_src_http_util_.md)

# Module: "src/http/util"

## Index

### Variables

* [safeMethods](_src_http_util_.md#const-safemethods)

### Functions

* [isSafeMethod](_src_http_util_.md#issafemethod)
* [parseContentType](_src_http_util_.md#parsecontenttype)
* [parseLink](_src_http_util_.md#parselink)

## Variables

### `Const` safeMethods

• **safeMethods**: *string[]* = ['GET', 'HEAD', 'OPTIONS', 'PRI', 'PROPFIND', 'REPORT', 'SEARCH', 'TRACE']

*Defined in [src/http/util.ts:45](https://github.com/evert/ketting/blob/f7a0a1b/src/http/util.ts#L45)*

## Functions

###  isSafeMethod

▸ **isSafeMethod**(`method`: string): *boolean*

*Defined in [src/http/util.ts:47](https://github.com/evert/ketting/blob/f7a0a1b/src/http/util.ts#L47)*

**Parameters:**

Name | Type |
------ | ------ |
`method` | string |

**Returns:** *boolean*

___

###  parseContentType

▸ **parseContentType**(`contentType`: string | null): *string | null*

*Defined in [src/http/util.ts:7](https://github.com/evert/ketting/blob/f7a0a1b/src/http/util.ts#L7)*

Takes a Content-Type header, and only returns the mime-type part.

**Parameters:**

Name | Type |
------ | ------ |
`contentType` | string &#124; null |

**Returns:** *string | null*

___

###  parseLink

▸ **parseLink**(`context`: string, `header`: string | null): *[Links](../classes/_src_link_.links.md)*

*Defined in [src/http/util.ts:20](https://github.com/evert/ketting/blob/f7a0a1b/src/http/util.ts#L20)*

**Parameters:**

Name | Type |
------ | ------ |
`context` | string |
`header` | string &#124; null |

**Returns:** *[Links](../classes/_src_link_.links.md)*
