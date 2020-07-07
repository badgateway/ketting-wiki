[ketting](../README.md) › [Globals](../globals.md) › ["src/action"](../modules/_src_action_.md) › [SimpleAction](_src_action_.simpleaction.md)

# Class: SimpleAction ‹**TFormData**›

## Type parameters

▪ **TFormData**

## Hierarchy

* **SimpleAction**

## Index

### Constructors

* [constructor](_src_action_.simpleaction.md#constructor)

### Properties

* [client](_src_action_.simpleaction.md#client)
* [href](_src_action_.simpleaction.md#href)
* [method](_src_action_.simpleaction.md#method)
* [type](_src_action_.simpleaction.md#type)

### Methods

* [submit](_src_action_.simpleaction.md#submit)

## Constructors

###  constructor

\+ **new SimpleAction**(`client`: [Client](_src_client_.client.md), `method`: string, `href`: string, `type`: string): *[SimpleAction](_src_action_.simpleaction.md)*

*Defined in [src/action.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/action.ts#L11)*

**Parameters:**

Name | Type |
------ | ------ |
`client` | [Client](_src_client_.client.md) |
`method` | string |
`href` | string |
`type` | string |

**Returns:** *[SimpleAction](_src_action_.simpleaction.md)*

## Properties

###  client

• **client**: *[Client](_src_client_.client.md)*

*Defined in [src/action.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/action.ts#L13)*

___

###  href

• **href**: *string*

*Defined in [src/action.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/action.ts#L13)*

___

###  method

• **method**: *string*

*Defined in [src/action.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/action.ts#L13)*

___

###  type

• **type**: *string*

*Defined in [src/action.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/action.ts#L13)*

## Methods

###  submit

▸ **submit**(`formData`: TFormData): *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹any››*

*Defined in [src/action.ts:17](https://github.com/evert/ketting/blob/f7a0a1b/src/action.ts#L17)*

**Parameters:**

Name | Type |
------ | ------ |
`formData` | TFormData |

**Returns:** *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹any››*
