[ketting](../README.md) › [Globals](../globals.md) › ["src/state/interface"](../modules/_src_state_interface_.md) › [State](_src_state_interface_.state.md)

# Interface: State ‹**T**›

## Type parameters

▪ **T**

## Hierarchy

* **State**

## Implemented by

* [BaseState](../classes/_src_state_base_state_.basestate.md)
* [BinaryState](../classes/_src_state_binary_.binarystate.md)
* [CjState](../classes/_src_state_collection_json_.cjstate.md)
* [HalState](../classes/_src_state_hal_.halstate.md)
* [HtmlState](../classes/_src_state_html_.htmlstate.md)
* [JsonApiState](../classes/_src_state_jsonapi_.jsonapistate.md)
* [SirenState](../classes/_src_state_siren_.sirenstate.md)
* [TextState](../classes/_src_state_text_.textstate.md)

## Index

### Properties

* [client](_src_state_interface_.state.md#client)
* [data](_src_state_interface_.state.md#data)
* [headers](_src_state_interface_.state.md#headers)
* [links](_src_state_interface_.state.md#links)
* [timestamp](_src_state_interface_.state.md#timestamp)
* [uri](_src_state_interface_.state.md#uri)

### Methods

* [clone](_src_state_interface_.state.md#clone)
* [contentHeaders](_src_state_interface_.state.md#contentheaders)
* [getEmbedded](_src_state_interface_.state.md#getembedded)
* [serializeBody](_src_state_interface_.state.md#serializebody)

## Properties

###  client

• **client**: *[Client](../classes/_src_client_.client.md)*

*Defined in [src/state/interface.ts:31](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L31)*

Reference to main client that created this state

___

###  data

• **data**: *T*

*Defined in [src/state/interface.ts:16](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L16)*

Represents the body of the HTTP response.

In the case of a JSON response, this will be deserialized

___

###  headers

• **headers**: *Headers*

*Defined in [src/state/interface.ts:26](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L26)*

The full list of HTTP headers that were sent with the response.

___

###  links

• **links**: *[Links](../classes/_src_link_.links.md)*

*Defined in [src/state/interface.ts:21](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L21)*

All links associated with the resource.

___

###  timestamp

• **timestamp**: *number*

*Defined in [src/state/interface.ts:66](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L66)*

Timestamp of when the State was first generated

___

###  uri

• **uri**: *string*

*Defined in [src/state/interface.ts:9](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L9)*

The URI associated with this state

## Methods

###  clone

▸ **clone**(): *[State](_src_state_interface_.state.md)‹T›*

*Defined in [src/state/interface.ts:68](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L68)*

**Returns:** *[State](_src_state_interface_.state.md)‹T›*

___

###  contentHeaders

▸ **contentHeaders**(): *Headers*

*Defined in [src/state/interface.ts:50](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L50)*

Content-headers are a subset of HTTP headers that related directly
to the content. The obvious ones are Content-Type.

This set of headers will be sent by the server along with a GET
response, but will also be sent back to the server in a PUT
request.

**Returns:** *Headers*

___

###  getEmbedded

▸ **getEmbedded**(): *[State](_src_state_interface_.state.md)[]*

*Defined in [src/state/interface.ts:61](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L61)*

Certain formats can embed other resources, identified by their
own URI.

When a format has embedded resources, we will use these to warm
the cache.

This method returns every embedded resource.

**Returns:** *[State](_src_state_interface_.state.md)[]*

___

###  serializeBody

▸ **serializeBody**(): *Buffer | Blob | string*

*Defined in [src/state/interface.ts:40](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L40)*

Returns a serialization of the state that can be used in a HTTP
response.

For example, a JSON object might simply serialize using
JSON.serialize().

**Returns:** *Buffer | Blob | string*
