[ketting](../README.md) › [Globals](../globals.md) › ["src/state/jsonapi"](_src_state_jsonapi_.md)

# Module: "src/state/jsonapi"

## Index

### Classes

* [JsonApiState](../classes/_src_state_jsonapi_.jsonapistate.md)

### Type aliases

* [JsonApiLink](_src_state_jsonapi_.md#jsonapilink)
* [JsonApiLinksObject](_src_state_jsonapi_.md#jsonapilinksobject)
* [JsonApiResource](_src_state_jsonapi_.md#jsonapiresource)
* [JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject)

### Functions

* [factory](_src_state_jsonapi_.md#const-factory)
* [parseJsonApiCollection](_src_state_jsonapi_.md#parsejsonapicollection)
* [parseJsonApiLink](_src_state_jsonapi_.md#parsejsonapilink)
* [parseJsonApiLinks](_src_state_jsonapi_.md#parsejsonapilinks)

## Type aliases

###  JsonApiLink

Ƭ **JsonApiLink**: *string | object*

*Defined in [src/state/jsonapi.ts:54](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L54)*

A JSON:API link can either be a string, or an object with at least a href
property.

___

###  JsonApiLinksObject

Ƭ **JsonApiLinksObject**: *object*

*Defined in [src/state/jsonapi.ts:60](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L60)*

This type is a full 'links' object, which might appear on the top level
or on resource objects.

#### Type declaration:

* \[ **rel**: *string*\]: [JsonApiLink](_src_state_jsonapi_.md#jsonapilink) | [JsonApiLink](_src_state_jsonapi_.md#jsonapilink)[] | undefined

* **profile**? : *[JsonApiLink](_src_state_jsonapi_.md#jsonapilink)*

* **self**? : *[JsonApiLink](_src_state_jsonapi_.md#jsonapilink)*

___

###  JsonApiResource

Ƭ **JsonApiResource**: *object*

*Defined in [src/state/jsonapi.ts:70](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L70)*

This is a single JSON:API resource. Its type contains just the properties
we care about.

#### Type declaration:

* **id**: *string*

* **links**? : *[JsonApiLinksObject](_src_state_jsonapi_.md#jsonapilinksobject)*

* **type**: *string*

___

###  JsonApiTopLevelObject

Ƭ **JsonApiTopLevelObject**: *object*

*Defined in [src/state/jsonapi.ts:82](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L82)*

This type represents a valid JSON:API response. We're only interested
in the links object at the moment, so everything else is (for now)
untyped.

#### Type declaration:

* \[ **s**: *string*\]: any

* **data**: *[JsonApiResource](_src_state_jsonapi_.md#jsonapiresource) | [JsonApiResource](_src_state_jsonapi_.md#jsonapiresource)[] | null*

* **links**? : *[JsonApiLinksObject](_src_state_jsonapi_.md#jsonapilinksobject)*

## Functions

### `Const` factory

▸ **factory**(`uri`: string, `response`: Response): *Promise‹[JsonApiState](../classes/_src_state_jsonapi_.jsonapistate.md)‹[JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject)››*

*Defined in [src/state/jsonapi.ts:32](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L32)*

Turns a HTTP response into a JsonApiState

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`response` | Response |

**Returns:** *Promise‹[JsonApiState](../classes/_src_state_jsonapi_.jsonapistate.md)‹[JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject)››*

___

###  parseJsonApiCollection

▸ **parseJsonApiCollection**(`contextUri`: string, `body`: [JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject)): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/jsonapi.ts:121](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L121)*

Find collection members in JSON:API objects.

A JSON:API top-level object might represent a collection that has 0 or more
members.

Members of this collection should appear as an 'item' link to the parent.

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | [JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject) |

**Returns:** *[Link](_src_link_.md#link)[]*

___

###  parseJsonApiLink

▸ **parseJsonApiLink**(`contextUri`: string, `rel`: string, `link`: [JsonApiLink](_src_state_jsonapi_.md#jsonapilink)): *[Link](_src_link_.md#link)*

*Defined in [src/state/jsonapi.ts:151](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L151)*

This function takes a single link value from a JSON:API link object, and
returns a object of type Link

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`rel` | string |
`link` | [JsonApiLink](_src_state_jsonapi_.md#jsonapilink) |

**Returns:** *[Link](_src_link_.md#link)*

___

###  parseJsonApiLinks

▸ **parseJsonApiLinks**(`contextUri`: string, `body`: [JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject)): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/jsonapi.ts:91](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L91)*

This function takes a JSON:API object, and extracts the links property.

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | [JsonApiTopLevelObject](_src_state_jsonapi_.md#jsonapitoplevelobject) |

**Returns:** *[Link](_src_link_.md#link)[]*
