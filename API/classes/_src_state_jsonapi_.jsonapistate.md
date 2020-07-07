[ketting](../README.md) › [Globals](../globals.md) › ["src/state/jsonapi"](../modules/_src_state_jsonapi_.md) › [JsonApiState](_src_state_jsonapi_.jsonapistate.md)

# Class: JsonApiState ‹**T**›

Represents a resource state in the HAL format

## Type parameters

▪ **T**

## Hierarchy

* [BaseState](_src_state_base_state_.basestate.md)‹T›

  ↳ **JsonApiState**

## Implements

* [State](../interfaces/_src_state_interface_.state.md)‹T›

## Index

### Constructors

* [constructor](_src_state_jsonapi_.jsonapistate.md#constructor)

### Properties

* [client](_src_state_jsonapi_.jsonapistate.md#client)
* [data](_src_state_jsonapi_.jsonapistate.md#data)
* [embedded](_src_state_jsonapi_.jsonapistate.md#protected-embedded)
* [headers](_src_state_jsonapi_.jsonapistate.md#headers)
* [links](_src_state_jsonapi_.jsonapistate.md#links)
* [timestamp](_src_state_jsonapi_.jsonapistate.md#timestamp)
* [uri](_src_state_jsonapi_.jsonapistate.md#uri)

### Methods

* [action](_src_state_jsonapi_.jsonapistate.md#action)
* [clone](_src_state_jsonapi_.jsonapistate.md#clone)
* [contentHeaders](_src_state_jsonapi_.jsonapistate.md#contentheaders)
* [getEmbedded](_src_state_jsonapi_.jsonapistate.md#getembedded)
* [serializeBody](_src_state_jsonapi_.jsonapistate.md#serializebody)

## Constructors

###  constructor

\+ **new JsonApiState**(`uri`: string, `data`: T, `headers`: Headers, `links`: [Links](_src_link_.links.md), `embedded?`: [State](../interfaces/_src_state_interface_.state.md)[]): *[JsonApiState](_src_state_jsonapi_.jsonapistate.md)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[constructor](_src_state_base_state_.basestate.md#constructor)*

*Defined in [src/state/base-state.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L38)*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`data` | T |
`headers` | Headers |
`links` | [Links](_src_link_.links.md) |
`embedded?` | [State](../interfaces/_src_state_interface_.state.md)[] |

**Returns:** *[JsonApiState](_src_state_jsonapi_.jsonapistate.md)*

## Properties

###  client

• **client**: *[Client](_src_client_.client.md)*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[client](../interfaces/_src_state_interface_.state.md#client)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[client](_src_state_base_state_.basestate.md#client)*

*Defined in [src/state/base-state.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L33)*

Reference to main client that created this state

___

###  data

• **data**: *T*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[data](../interfaces/_src_state_interface_.state.md#data)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[data](_src_state_base_state_.basestate.md#data)*

*Defined in [src/state/base-state.ts:18](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L18)*

Represents the body of the HTTP response.

In the case of a JSON response, this will be deserialized

___

### `Protected` embedded

• **embedded**: *[State](../interfaces/_src_state_interface_.state.md)[]*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[embedded](_src_state_base_state_.basestate.md#protected-embedded)*

*Defined in [src/state/base-state.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L38)*

Embedded resoureces

___

###  headers

• **headers**: *Headers*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[headers](../interfaces/_src_state_interface_.state.md#headers)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[headers](_src_state_base_state_.basestate.md#headers)*

*Defined in [src/state/base-state.ts:23](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L23)*

The full list of HTTP headers that were sent with the response.

___

###  links

• **links**: *[Links](_src_link_.links.md)*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[links](../interfaces/_src_state_interface_.state.md#links)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[links](_src_state_base_state_.basestate.md#links)*

*Defined in [src/state/base-state.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L28)*

All links associated with the resource.

___

###  timestamp

• **timestamp**: *number*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[timestamp](../interfaces/_src_state_interface_.state.md#timestamp)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[timestamp](_src_state_base_state_.basestate.md#timestamp)*

*Defined in [src/state/base-state.ts:115](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L115)*

Timestamp of when the State was first generated

___

###  uri

• **uri**: *string*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[uri](../interfaces/_src_state_interface_.state.md#uri)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[uri](_src_state_base_state_.basestate.md#uri)*

*Defined in [src/state/base-state.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L11)*

The URI associated with this state

## Methods

###  action

▸ **action**‹**TFormData**›(`name?`: undefined | string): *[Action](../interfaces/_src_action_.action.md)‹TFormData›*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[action](_src_state_base_state_.basestate.md#action)*

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

###  clone

▸ **clone**(): *[JsonApiState](_src_state_jsonapi_.jsonapistate.md)‹T›*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Overrides [BaseState](_src_state_base_state_.basestate.md).[clone](_src_state_base_state_.basestate.md#abstract-clone)*

*Defined in [src/state/jsonapi.ts:16](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L16)*

**Returns:** *[JsonApiState](_src_state_jsonapi_.jsonapistate.md)‹T›*

___

###  contentHeaders

▸ **contentHeaders**(): *Headers*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[contentHeaders](_src_state_base_state_.basestate.md#contentheaders)*

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

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[getEmbedded](_src_state_base_state_.basestate.md#getembedded)*

*Defined in [src/state/base-state.ts:106](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L106)*

Certain formats can embed other resources, identified by their
own URI.

When a format has embedded resources, we will use these to warm
the cache.

This method returns every embedded resource.

**Returns:** *[State](../interfaces/_src_state_interface_.state.md)[]*

___

###  serializeBody

▸ **serializeBody**(): *string*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Overrides [BaseState](_src_state_base_state_.basestate.md).[serializeBody](_src_state_base_state_.basestate.md#abstract-serializebody)*

*Defined in [src/state/jsonapi.ts:10](https://github.com/evert/ketting/blob/f7a0a1b/src/state/jsonapi.ts#L10)*

**Returns:** *string*
