[ketting](../README.md) › [Globals](../globals.md) › ["src/state/hal"](_src_state_hal_.md)

# Module: "src/state/hal"

## Index

### Classes

* [HalState](../classes/_src_state_hal_.halstate.md)

### Functions

* [factory](_src_state_hal_.md#const-factory)
* [parseHalEmbedded](_src_state_hal_.md#parsehalembedded)
* [parseHalLink](_src_state_hal_.md#parsehallink)
* [parseHalLinks](_src_state_hal_.md#parsehallinks)

## Functions

### `Const` factory

▸ **factory**(`uri`: string, `response`: Response): *Promise‹[HalState](../classes/_src_state_hal_.halstate.md)‹HalResource››*

*Defined in [src/state/hal.ts:68](https://github.com/evert/ketting/blob/f7a0a1b/src/state/hal.ts#L68)*

Turns a HTTP response into a HalState

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`response` | Response |

**Returns:** *Promise‹[HalState](../classes/_src_state_hal_.halstate.md)‹HalResource››*

___

###  parseHalEmbedded

▸ **parseHalEmbedded**(`context`: string, `body`: HalResource, `headers`: Headers): *[HalState](../classes/_src_state_hal_.halstate.md)‹any›[]*

*Defined in [src/state/hal.ts:185](https://github.com/evert/ketting/blob/f7a0a1b/src/state/hal.ts#L185)*

Parse the HAL _embedded object. Right now we're just grabbing the
information from _embedded and turn it into links.

**Parameters:**

Name | Type |
------ | ------ |
`context` | string |
`body` | HalResource |
`headers` | Headers |

**Returns:** *[HalState](../classes/_src_state_hal_.halstate.md)‹any›[]*

___

###  parseHalLink

▸ **parseHalLink**(`context`: string, `rel`: string, `links`: HalLink[]): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/hal.ts:165](https://github.com/evert/ketting/blob/f7a0a1b/src/state/hal.ts#L165)*

Parses a single HAL link from a _links object

**Parameters:**

Name | Type |
------ | ------ |
`context` | string |
`rel` | string |
`links` | HalLink[] |

**Returns:** *[Link](_src_link_.md#link)[]*

___

###  parseHalLinks

▸ **parseHalLinks**(`context`: string, `body`: HalResource): *[Link](_src_link_.md#link)[]*

*Defined in [src/state/hal.ts:95](https://github.com/evert/ketting/blob/f7a0a1b/src/state/hal.ts#L95)*

Parse the Hal _links object and populate the 'links' property.

**Parameters:**

Name | Type |
------ | ------ |
`context` | string |
`body` | HalResource |

**Returns:** *[Link](_src_link_.md#link)[]*
