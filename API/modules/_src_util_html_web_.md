[ketting](../README.md) › [Globals](../globals.md) › ["src/util/html.web"](_src_util_html_web_.md)

# Module: "src/util/html.web"

## Index

### Type aliases

* [HtmlForm](_src_util_html_web_.md#htmlform)
* [ParseHtmlResult](_src_util_html_web_.md#parsehtmlresult)

### Functions

* [formFromTags](_src_util_html_web_.md#formfromtags)
* [linkFromTags](_src_util_html_web_.md#linkfromtags)
* [parseHtml](_src_util_html_web_.md#parsehtml)

## Type aliases

###  HtmlForm

Ƭ **HtmlForm**: *object*

*Defined in [src/util/html.web.ts:4](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.web.ts#L4)*

#### Type declaration:

* **action**: *string*

* **enctype**: *string | null*

* **id**: *string | null*

* **method**: *string | null*

* **rel**: *string | null*

___

###  ParseHtmlResult

Ƭ **ParseHtmlResult**: *object*

*Defined in [src/util/html.web.ts:12](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.web.ts#L12)*

#### Type declaration:

* **forms**: *[HtmlForm](_src_util_html_web_.md#htmlform)[]*

* **links**: *[Link](_src_link_.md#link)[]*

## Functions

###  formFromTags

▸ **formFromTags**(`contextUri`: string, `elements`: HTMLCollectionOf‹HTMLFormElement›): *[HtmlForm](_src_util_html_web_.md#htmlform)[]*

*Defined in [src/util/html.web.ts:73](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.web.ts#L73)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`elements` | HTMLCollectionOf‹HTMLFormElement› |

**Returns:** *[HtmlForm](_src_util_html_web_.md#htmlform)[]*

___

###  linkFromTags

▸ **linkFromTags**(`contextUri`: string, `elements`: HTMLCollectionOf‹HTMLElement›): *[Link](_src_link_.md#link)[]*

*Defined in [src/util/html.web.ts:42](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.web.ts#L42)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`elements` | HTMLCollectionOf‹HTMLElement› |

**Returns:** *[Link](_src_link_.md#link)[]*

___

###  parseHtml

▸ **parseHtml**(`contextUri`: string, `body`: string): *[ParseHtmlResult](_src_util_html_web_.md#parsehtmlresult)*

*Defined in [src/util/html.web.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/util/html.web.ts#L18)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | string |

**Returns:** *[ParseHtmlResult](_src_util_html_web_.md#parsehtmlresult)*
