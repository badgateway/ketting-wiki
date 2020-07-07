[ketting](../README.md) › [Globals](../globals.md) › ["src/state/head"](_src_state_head_.md)

# Module: "src/state/head"

## Index

### Functions

* [factory](_src_state_head_.md#const-factory)

## Functions

### `Const` factory

▸ **factory**(`uri`: string, `response`: Response): *Promise‹[HeadState](../interfaces/_src_state_interface_.headstate.md)›*

*Defined in [src/state/head.ts:10](https://github.com/evert/ketting/blob/f7a0a1b/src/state/head.ts#L10)*

Turns the response to a HTTP Head request into a HeadState object.

HeadState is a bit different from normal State objects, because it's
missing a bunch of information.

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`response` | Response |

**Returns:** *Promise‹[HeadState](../interfaces/_src_state_interface_.headstate.md)›*
