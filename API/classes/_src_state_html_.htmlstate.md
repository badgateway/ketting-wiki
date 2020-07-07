[ketting](../README.md) › [Globals](../globals.md) › ["src/state/html"](../modules/_src_state_html_.md) › [HtmlState](_src_state_html_.htmlstate.md)

# Class: HtmlState

Represents a resource state in the HAL format

## Hierarchy

* [BaseState](_src_state_base_state_.basestate.md)‹string›

  ↳ **HtmlState**

## Implements

* [State](../interfaces/_src_state_interface_.state.md)‹string›

## Index

### Constructors

* [constructor](_src_state_html_.htmlstate.md#constructor)

### Properties

* [client](_src_state_html_.htmlstate.md#client)
* [data](_src_state_html_.htmlstate.md#data)
* [embedded](_src_state_html_.htmlstate.md#protected-embedded)
* [forms](_src_state_html_.htmlstate.md#private-forms)
* [headers](_src_state_html_.htmlstate.md#headers)
* [links](_src_state_html_.htmlstate.md#links)
* [timestamp](_src_state_html_.htmlstate.md#timestamp)
* [uri](_src_state_html_.htmlstate.md#uri)

### Methods

* [action](_src_state_html_.htmlstate.md#action)
* [clone](_src_state_html_.htmlstate.md#clone)
* [contentHeaders](_src_state_html_.htmlstate.md#contentheaders)
* [getEmbedded](_src_state_html_.htmlstate.md#getembedded)
* [serializeBody](_src_state_html_.htmlstate.md#serializebody)

## Constructors

###  constructor

\+ **new HtmlState**(`uri`: string, `body`: string, `headers`: Headers, `links`: [Links](_src_link_.links.md), `forms`: [HtmlForm](../modules/_src_util_html_.md#htmlform)[]): *[HtmlState](_src_state_html_.htmlstate.md)*

*Overrides [BaseState](_src_state_base_state_.basestate.md).[constructor](_src_state_base_state_.basestate.md#constructor)*

*Defined in [src/state/html.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/state/html.ts#L13)*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`body` | string |
`headers` | Headers |
`links` | [Links](_src_link_.links.md) |
`forms` | [HtmlForm](../modules/_src_util_html_.md#htmlform)[] |

**Returns:** *[HtmlState](_src_state_html_.htmlstate.md)*

## Properties

###  client

• **client**: *[Client](_src_client_.client.md)*

*Implementation of [State](../interfaces/_src_state_interface_.state.md).[client](../interfaces/_src_state_interface_.state.md#client)*

*Inherited from [BaseState](_src_state_base_state_.basestate.md).[client](_src_state_base_state_.basestate.md#client)*

*Defined in [src/state/base-state.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/state/base-state.ts#L33)*

Reference to main client that created this state

___

###  data

• **data**: *string*

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

### `Private` forms

• **forms**: *[HtmlForm](../modules/_src_util_html_.md#htmlform)[]*

*Defined in [src/state/html.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/state/html.ts#L13)*

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

*Overrides [BaseState](_src_state_base_state_.basestate.md).[action](_src_state_base_state_.basestate.md#action)*

*Defined in [src/state/html.ts:49](https://github.com/evert/ketting/blob/f7a0a1b/src/state/html.ts#L49)*

Return an action by name.

Actions in HTML are HTML <form> tags.

If no name is given, the first HTML form is returned.

**Type parameters:**

▪ **TFormData**

**Parameters:**

Name | Type |
------ | ------ |
`name?` | undefined &#124; string |

**Returns:** *[Action](../interfaces/_src_action_.action.md)‹TFormData›*

___

###  clone

▸ **clone**(): *[HtmlState](_src_state_html_.htmlstate.md)*

*Implementation of [State](../interfaces/_src_state_interface_.state.md)*

*Overrides [BaseState](_src_state_base_state_.basestate.md).[clone](_src_state_base_state_.basestate.md#abstract-clone)*

*Defined in [src/state/html.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/state/html.ts#L28)*

**Returns:** *[HtmlState](_src_state_html_.htmlstate.md)*

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

*Defined in [src/state/html.ts:22](https://github.com/evert/ketting/blob/f7a0a1b/src/state/html.ts#L22)*

**Returns:** *string*
