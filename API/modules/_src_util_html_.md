[ketting](../README.md) › [Globals](../globals.md) › ["src/util/html"](_src_util_html_.md)

# Module: "src/util/html"

## Index

### Type aliases

* [HtmlForm](_src_util_html_.md#htmlform)
* [ParseHtmlResult](_src_util_html_.md#parsehtmlresult)

### Functions

* [parseForm](_src_util_html_.md#parseform)
* [parseHtml](_src_util_html_.md#parsehtml)
* [parseLink](_src_util_html_.md#parselink)

## Type aliases

###  HtmlForm

Ƭ **HtmlForm**: *object*

*Defined in [src/util/html.ts:5](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.ts#L5)*

#### Type declaration:

* **action**: *string*

* **enctype**: *string | null*

* **id**: *string | null*

* **method**: *string | null*

* **rel**: *string | null*

___

###  ParseHtmlResult

Ƭ **ParseHtmlResult**: *object*

*Defined in [src/util/html.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.ts#L13)*

#### Type declaration:

* **forms**: *[HtmlForm](_src_util_html_.md#htmlform)[]*

* **links**: *[Link](_src_link_.md#link)[]*

## Functions

###  parseForm

▸ **parseForm**(`contextUri`: string, `node`: Tag): *[HtmlForm](_src_util_html_.md#htmlform)[]*

*Defined in [src/util/html.ts:78](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.ts#L78)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`node` | Tag |

**Returns:** *[HtmlForm](_src_util_html_.md#htmlform)[]*

___

###  parseHtml

▸ **parseHtml**(`contextUri`: string, `body`: string): *[ParseHtmlResult](_src_util_html_.md#parsehtmlresult)*

*Defined in [src/util/html.ts:20](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.ts#L20)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | string |

**Returns:** *[ParseHtmlResult](_src_util_html_.md#parsehtmlresult)*

___

###  parseLink

▸ **parseLink**(`contextUri`: string, `node`: Tag): *[Link](_src_link_.md#link)[]*

*Defined in [src/util/html.ts:50](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.ts#L50)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`node` | Tag |

**Returns:** *[Link](_src_link_.md#link)[]*
