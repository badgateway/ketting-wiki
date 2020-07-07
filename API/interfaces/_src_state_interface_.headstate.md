[ketting](../README.md) › [Globals](../globals.md) › ["src/state/interface"](../modules/_src_state_interface_.md) › [HeadState](_src_state_interface_.headstate.md)

# Interface: HeadState

HeadState represents the response to a HEAD request.

Some information in HEAD responses might be available, but many aren't.
Notably, the body.

## Hierarchy

* **HeadState**

## Index

### Properties

* [headers](_src_state_interface_.headstate.md#headers)
* [links](_src_state_interface_.headstate.md#links)
* [timestamp](_src_state_interface_.headstate.md#timestamp)
* [uri](_src_state_interface_.headstate.md#uri)

### Methods

* [contentHeaders](_src_state_interface_.headstate.md#contentheaders)

## Properties

###  headers

• **headers**: *Headers*

*Defined in [src/state/interface.ts:93](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L93)*

The full list of HTTP headers that were sent with the response.

___

###  links

• **links**: *[Links](../classes/_src_link_.links.md)*

*Defined in [src/state/interface.ts:88](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L88)*

All links associated with the resource.

___

###  timestamp

• **timestamp**: *number*

*Defined in [src/state/interface.ts:108](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L108)*

Timestamp of when the State was first generated

___

###  uri

• **uri**: *string*

*Defined in [src/state/interface.ts:83](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L83)*

The URI associated with this state

## Methods

###  contentHeaders

▸ **contentHeaders**(): *Headers*

*Defined in [src/state/interface.ts:103](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L103)*

Content-headers are a subset of HTTP headers that related directly
to the content. The obvious ones are Content-Type.

This set of headers will be sent by the server along with a GET
response, but will also be sent back to the server in a PUT
request.

**Returns:** *Headers*
