[ketting](../README.md) › [Globals](../globals.md) › ["src/state/interface"](_src_state_interface_.md)

# Module: "src/state/interface"

## Index

### Interfaces

* [HeadState](../interfaces/_src_state_interface_.headstate.md)
* [State](../interfaces/_src_state_interface_.state.md)

### Type aliases

* [StateFactory](_src_state_interface_.md#statefactory)

### Functions

* [isState](_src_state_interface_.md#isstate)

## Type aliases

###  StateFactory

Ƭ **StateFactory**: *function*

*Defined in [src/state/interface.ts:116](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L116)*

A 'StateFactory' is responsible for taking a Fetch Response, and returning
an object that impements the State interface

#### Type declaration:

▸ (`uri`: string, `request`: Response): *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹T››*

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`request` | Response |

## Functions

###  isState

▸ **isState**(`input`: Record‹string, any›): *input is State*

*Defined in [src/state/interface.ts:118](https://github.com/evert/ketting/blob/f7a0a1b/src/state/interface.ts#L118)*

**Parameters:**

Name | Type |
------ | ------ |
`input` | Record‹string, any› |

**Returns:** *input is State*
