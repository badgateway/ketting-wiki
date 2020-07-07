[ketting](../README.md) › [Globals](../globals.md) › ["src/state/collection-json"](_src_state_collection_json_.md)

# Module: "src/state/collection-json"

## Index

### Classes

* [CjState](../classes/_src_state_collection_json_.cjstate.md)

### Type aliases

* [CjCollection](_src_state_collection_json_.md#cjcollection)
* [CjDocument](_src_state_collection_json_.md#cjdocument)
* [CjError](_src_state_collection_json_.md#cjerror)
* [CjItem](_src_state_collection_json_.md#cjitem)
* [CjLink](_src_state_collection_json_.md#cjlink)
* [CjProperty](_src_state_collection_json_.md#cjproperty)
* [CjQuery](_src_state_collection_json_.md#cjquery)
* [CjTemplate](_src_state_collection_json_.md#cjtemplate)

### Functions

* [factory](_src_state_collection_json_.md#const-factory)
* [parseCjLinks](_src_state_collection_json_.md#parsecjlinks)

## Type aliases

###  CjCollection

Ƭ **CjCollection**: *object*

*Defined in [src/state/collection-json.ts:60](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L60)*

#### Type declaration:

* **error**? : *[CjError](_src_state_collection_json_.md#cjerror)*

* **href**? : *undefined | string*

* **items**? : *[CjItem](_src_state_collection_json_.md#cjitem)[]*

* **links**? : *[CjLink](_src_state_collection_json_.md#cjlink)[]*

* **queries**? : *[CjQuery](_src_state_collection_json_.md#cjquery)[]*

* **template**? : *[CjTemplate](_src_state_collection_json_.md#cjtemplate)*

* **version**? : *undefined | string*

___

###  CjDocument

Ƭ **CjDocument**: *object*

*Defined in [src/state/collection-json.ts:56](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L56)*

#### Type declaration:

* **collection**: *[CjCollection](_src_state_collection_json_.md#cjcollection)*

___

###  CjError

Ƭ **CjError**: *object*

*Defined in [src/state/collection-json.ts:70](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L70)*

#### Type declaration:

* **code**? : *undefined | string*

* **message**? : *undefined | string*

* **title**? : *undefined | string*

___

###  CjItem

Ƭ **CjItem**: *object*

*Defined in [src/state/collection-json.ts:80](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L80)*

#### Type declaration:

* **data**? : *[CjProperty](_src_state_collection_json_.md#cjproperty)[]*

* **href**? : *undefined | string*

* **links**? : *[CjLink](_src_state_collection_json_.md#cjlink)[]*

___

###  CjLink

Ƭ **CjLink**: *object*

*Defined in [src/state/collection-json.ts:100](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L100)*

#### Type declaration:

* **href**: *string*

* **name**? : *undefined | string*

* **prompt**? : *undefined | string*

* **rel**: *string*

* **render**? : *"image" | "link"*

___

###  CjProperty

Ƭ **CjProperty**: *object*

*Defined in [src/state/collection-json.ts:86](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L86)*

#### Type declaration:

* **name**: *string*

* **prompt**? : *undefined | string*

* **value**? : *undefined | string*

___

###  CjQuery

Ƭ **CjQuery**: *object*

*Defined in [src/state/collection-json.ts:92](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L92)*

#### Type declaration:

* **data**? : *[CjProperty](_src_state_collection_json_.md#cjproperty)[]*

* **href**: *string*

* **name**? : *undefined | string*

* **prompt**? : *undefined | string*

* **rel**: *string*

___

###  CjTemplate

Ƭ **CjTemplate**: *object*

*Defined in [src/state/collection-json.ts:76](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L76)*

#### Type declaration:

* **data**? : *[CjProperty](_src_state_collection_json_.md#cjproperty)[]*

## Functions

### `Const` factory

▸ **factory**(`uri`: string, `response`: Response): *Promise‹[CjState](../classes/_src_state_collection_json_.cjstate.md)‹[CjCollection](_src_state_collection_json_.md#cjcollection)››*

*Defined in [src/state/collection-json.ts:31](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L31)*

Turns a HTTP response into a CjState

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`response` | Response |

**Returns:** *Promise‹[CjState](../classes/_src_state_collection_json_.cjstate.md)‹[CjCollection](_src_state_collection_json_.md#cjcollection)››*

___

###  parseCjLinks

▸ **parseCjLinks**(`contextUri`: string, `body`: [CjDocument](_src_state_collection_json_.md#cjdocument)): *object[]*

*Defined in [src/state/collection-json.ts:109](https://github.com/evert/ketting/blob/f7a0a1b/src/state/collection-json.ts#L109)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | [CjDocument](_src_state_collection_json_.md#cjdocument) |

**Returns:** *object[]*
