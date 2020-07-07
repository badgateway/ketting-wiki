[ketting](../README.md) › [Globals](../globals.md) › ["src/state/siren"](_src_state_siren_.md)

# Module: "src/state/siren"

## Index

### Classes

* [SirenState](../classes/_src_state_siren_.sirenstate.md)

### Type aliases

* [SirenAction](_src_state_siren_.md#sirenaction)
* [SirenEntity](_src_state_siren_.md#sirenentity)
* [SirenField](_src_state_siren_.md#sirenfield)
* [SirenLink](_src_state_siren_.md#sirenlink)
* [SirenProperties](_src_state_siren_.md#sirenproperties)
* [SirenSubEntity](_src_state_siren_.md#sirensubentity)

### Functions

* [factory](_src_state_siren_.md#const-factory)
* [isSubEntity](_src_state_siren_.md#issubentity)
* [parseSirenEmbedded](_src_state_siren_.md#parsesirenembedded)
* [parseSirenLink](_src_state_siren_.md#parsesirenlink)
* [parseSirenLinks](_src_state_siren_.md#parsesirenlinks)
* [parseSirenSubEntityAsEmbedded](_src_state_siren_.md#parsesirensubentityasembedded)
* [parseSirenSubEntityAsLink](_src_state_siren_.md#parsesirensubentityaslink)

## Type aliases

###  SirenAction

Ƭ **SirenAction**: *object*

*Defined in [src/state/siren.ts:124](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L124)*

#### Type declaration:

* **class**? : *string[]*

* **fields**? : *[SirenField](_src_state_siren_.md#sirenfield)[]*

* **href**: *string*

* **method**? : *undefined | string*

* **name**: *string*

* **title**? : *undefined | string*

* **type**? : *undefined | string*

___

###  SirenEntity

Ƭ **SirenEntity**: *object*

*Defined in [src/state/siren.ts:99](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L99)*

#### Type declaration:

* **actions**? : *[SirenAction](_src_state_siren_.md#sirenaction)[]*

* **class**? : *string[]*

* **entities**? : *object | [SirenEntity](_src_state_siren_.md#sirenentity) & object[]*

* **links**? : *[SirenLink](_src_state_siren_.md#sirenlink)[]*

* **properties**: *T*

* **title**? : *undefined | string*

___

###  SirenField

Ƭ **SirenField**: *object*

*Defined in [src/state/siren.ts:134](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L134)*

#### Type declaration:

* **class**? : *string[]*

* **name**: *string*

* **title**? : *undefined | string*

* **type**? : *"hidden" | "text" | "search" | "tel" | "url" | "email" | "password" | "datetime" | "date" | "month" | "week" | "time" | "datetime-local" | "number" | "range" | "color" | "checkbox" | "radio" | "file"*

* **value**? : *undefined | string*

___

###  SirenLink

Ƭ **SirenLink**: *object*

*Defined in [src/state/siren.ts:114](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L114)*

#### Type declaration:

* **class**? : *string[]*

* **href**: *string*

* **rel**: *string[]*

* **title**? : *undefined | string*

* **type**? : *undefined | string*

___

###  SirenProperties

Ƭ **SirenProperties**: *Record‹string, any› | undefined*

*Defined in [src/state/siren.ts:97](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L97)*

___

###  SirenSubEntity

Ƭ **SirenSubEntity**: *[SirenEntity](_src_state_siren_.md#sirenentity)‹any› & object*

*Defined in [src/state/siren.ts:112](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L112)*

## Functions

### `Const` factory

▸ **factory**(`uri`: string, `response`: Response): *Promise‹[SirenState](../classes/_src_state_siren_.sirenstate.md)‹any››*

*Defined in [src/state/siren.ts:80](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L80)*

Turns a HTTP response into a SirenState

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`response` | Response |

**Returns:** *Promise‹[SirenState](../classes/_src_state_siren_.sirenstate.md)‹any››*

___

###  isSubEntity

▸ **isSubEntity**(`input`: [SirenLink](_src_state_siren_.md#sirenlink) | [SirenSubEntity](_src_state_siren_.md#sirensubentity)): *input is SirenSubEntity*

*Defined in [src/state/siren.ts:271](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L271)*

**Parameters:**

Name | Type |
------ | ------ |
`input` | [SirenLink](_src_state_siren_.md#sirenlink) &#124; [SirenSubEntity](_src_state_siren_.md#sirensubentity) |

**Returns:** *input is SirenSubEntity*

___

###  parseSirenEmbedded

▸ **parseSirenEmbedded**(`contextUri`: string, `body`: [SirenEntity](_src_state_siren_.md#sirenentity)‹any›, `headers`: Headers): *[SirenState](../classes/_src_state_siren_.sirenstate.md)‹[SirenEntity](_src_state_siren_.md#sirenentity)‹any››[]*

*Defined in [src/state/siren.ts:189](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L189)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | [SirenEntity](_src_state_siren_.md#sirenentity)‹any› |
`headers` | Headers |

**Returns:** *[SirenState](../classes/_src_state_siren_.sirenstate.md)‹[SirenEntity](_src_state_siren_.md#sirenentity)‹any››[]*

___

###  parseSirenLink

▸ **parseSirenLink**(`contextUri`: string, `link`: [SirenLink](_src_state_siren_.md#sirenlink)): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/siren.ts:166](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L166)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`link` | [SirenLink](_src_state_siren_.md#sirenlink) |

**Returns:** *[Link](_src_link_.md#link)[]*

___

###  parseSirenLinks

▸ **parseSirenLinks**(`contextUri`: string, `body`: [SirenEntity](_src_state_siren_.md#sirenentity)‹any›): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/siren.ts:142](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L142)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`body` | [SirenEntity](_src_state_siren_.md#sirenentity)‹any› |

**Returns:** *[Link](_src_link_.md#link)[]*

___

###  parseSirenSubEntityAsEmbedded

▸ **parseSirenSubEntityAsEmbedded**(`contextUri`: string, `subEntity`: [SirenSubEntity](_src_state_siren_.md#sirensubentity), `headers`: Headers): *[SirenState](../classes/_src_state_siren_.sirenstate.md)‹[SirenEntity](_src_state_siren_.md#sirenentity)‹any›› | null*

*Defined in [src/state/siren.ts:242](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L242)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`subEntity` | [SirenSubEntity](_src_state_siren_.md#sirensubentity) |
`headers` | Headers |

**Returns:** *[SirenState](../classes/_src_state_siren_.sirenstate.md)‹[SirenEntity](_src_state_siren_.md#sirenentity)‹any›› | null*

___

###  parseSirenSubEntityAsLink

▸ **parseSirenSubEntityAsLink**(`contextUri`: string, `subEntity`: [SirenSubEntity](_src_state_siren_.md#sirensubentity)): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/siren.ts:210](https://github.com/evert/ketting/blob/f7a0a1b/src/state/siren.ts#L210)*

**Parameters:**

Name | Type |
------ | ------ |
`contextUri` | string |
`subEntity` | [SirenSubEntity](_src_state_siren_.md#sirensubentity) |

**Returns:** *[Link](_src_link_.md#link)[]*
