[ketting](../README.md) › [Globals](../globals.md) › ["src/state/base-state"](../modules/_src_state_base_state_.md) › [BaseState](_src_state_base_state_.basestate.md)

# Class: BaseState ‹**T**›

## Type parameters

▪ **T**

## Hierarchy

* **BaseState**

  ↳ [HalState](_src_state_hal_.halstate.md)

  ↳ [BinaryState](_src_state_binary_.binarystate.md)

  ↳ [JsonApiState](_src_state_jsonapi_.jsonapistate.md)

  ↳ [SirenState](_src_state_siren_.sirenstate.md)

  ↳ [TextState](_src_state_text_.textstate.md)

  ↳ [CjState](_src_state_collection_json_.cjstate.md)

  ↳ [HtmlState](_src_state_html_.htmlstate.md)

## Implements

* [State](../interfaces/_src_state_interface_.state.md)‹T›

## Index

### Constructors

* [constructor](_src_state_base_state_.basestate.md#constructor)

### Properties

* [client](_src_state_base_state_.basestate.md#client)
* [data](_src_state_base_state_.basestate.md#data)
* [embedded](_src_state_base_state_.basestate.md#protected-embedded)
* [headers](_src_state_base_state_.basestate.md#headers)
* [links](_src_state_base_state_.basestate.md#links)
* [timestamp](_src_state_base_state_.basestate.md#timestamp)
* [uri](_src_state_base_state_.basestate.md#uri)

### Methods

* [action](_src_state_base_state_.basestate.md#action)
* [clone](_src_state_base_state_.basestate.md#abstract-clone)
* [contentHeaders](_src_state_base_state_.basestate.md#contentheaders)
* [getEmbedded](_src_state_base_state_.basestate.md#getembedded)
* [serializeBody](_src_state_base_state_.basestate.md#abstract-serializebody)

## Constructors

###  constructor

\+ **new BaseState**(`uri`: string, `data`: T, `headers`: Headers, `links`: [Links](_src_link_.links.md), `embedded?`: [State](../interfaces/_src_state_interface_.state.md)[]): *[BaseState](_src_state_base_state_.basestate.md)*

*Defined in [src/state/base-state.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L38)*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`data` | T |
`headers` | Headers |
`links` | [Links](_src_link_.links.md) |
`embedded?` | [State](../interfaces/_src_state_interface_.state.md)[] |

**Returns:** *[BaseState](_src_state_base_state_.basestate.md)*

## Properties

###  client

• **client**: *[Client](_src_client_.client.md)*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[client](../interfaces/_src_state_interface_.state.md#client)*

*Defined in [src/state/base-state.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L33)*

Reference to main client that created this state

___

###  data

• **data**: *T*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[data](../interfaces/_src_state_interface_.state.md#data)*

*Defined in [src/state/base-state.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L18)*

Represents the body of the HTTP response.

In the case of a JSON response, this will be deserialized

___

### `Protected` embedded

• **embedded**: *[State](../interfaces/_src_state_interface_.state.md)[]*

*Defined in [src/state/base-state.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L38)*

Embedded resoureces

___

###  headers

• **headers**: *Headers*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[headers](../interfaces/_src_state_interface_.state.md#headers)*

*Defined in [src/state/base-state.ts:23](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L23)*

The full list of HTTP headers that were sent with the response.

___

###  links

• **links**: *[Links](_src_link_.links.md)*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[links](../interfaces/_src_state_interface_.state.md#links)*

*Defined in [src/state/base-state.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L28)*

All links associated with the resource.

___

###  timestamp

• **timestamp**: *number*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[timestamp](../interfaces/_src_state_interface_.state.md#timestamp)*

*Defined in [src/state/base-state.ts:115](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L115)*

Timestamp of when the State was first generated

___

###  uri

• **uri**: *string*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[uri](../interfaces/_src_state_interface_.state.md#uri)*

*Defined in [src/state/base-state.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L11)*

The URI associated with this state

## Methods

###  action

▸ **action**‹**TFormData**›(`name?`: undefined | string): *[Action](../interfaces/_src_action_.action.md)‹TFormData›*

*Defined in [src/state/base-state.ts:82](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L82)*

Return an action by name.

If the format provides a default action, the name may be omitted.

**Type parameters:**

▪ **TFormData**

**Parameters:**

Name | Type |
------ | ------ |
`name?` | undefined &#124; string |

**Returns:** *[Action](../interfaces/_src_action_.action.md)‹TFormData›*

___

### `Abstract` clone

▸ **clone**(): *[State](../interfaces/_src_state_interface_.state.md)‹T›*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Defined in [src/state/base-state.ts:117](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L117)*

**Returns:** *[State](../interfaces/_src_state_interface_.state.md)‹T›*

___

###  contentHeaders

▸ **contentHeaders**(): *Headers*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Defined in [src/state/base-state.ts:59](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L59)*

Content-headers are a subset of HTTP headers that related directly
to the content. The obvious ones are Content-Type.

This set of headers will be sent by the server along with a GET
response, but will also be sent back to the server in a PUT
request.

**Returns:** *Headers*

___

###  getEmbedded

▸ **getEmbedded**(): *[State](../interfaces/_src_state_interface_.state.md)[]*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Defined in [src/state/base-state.ts:106](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L106)*

Certain formats can embed other resources, identified by their
own URI.

When a format has embedded resources, we will use these to warm
the cache.

This method returns every embedded resource.

**Returns:** *[State](../interfaces/_src_state_interface_.state.md)[]*

___

### `Abstract` serializeBody

▸ **serializeBody**(): *Buffer | Blob | string*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Defined in [src/state/base-state.ts:95](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L95)*

Returns a serialization of the state that can be used in a HTTP
response.

For example, a JSON object might simply serialize using
JSON.serialize().

**Returns:** *Buffer | Blob | string*
