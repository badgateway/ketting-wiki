[ketting](../README.md) › [Globals](../globals.md) › ["src/link"](_src_link_.md)

# Module: "src/link"

## Index

### Classes

* [LinkNotFound](../classes/_src_link_.linknotfound.md)
* [Links](../classes/_src_link_.links.md)

### Type aliases

* [Link](_src_link_.md#link)
* [LinkVariables](_src_link_.md#linkvariables)
* [NewLink](_src_link_.md#newlink)

## Type aliases

###  Link

Ƭ **Link**: *object*

*Defined in [src/link.ts:1](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L1)*

#### Type declaration:

* **anchor**? : *undefined | string*

* **context**: *string*

* **href**: *string*

* **hreflang**? : *undefined | string*

* **media**? : *undefined | string*

* **rel**: *string*

* **templated**? : *undefined | false | true*

* **title**? : *undefined | string*

* **type**? : *undefined | string*

___

###  LinkVariables

Ƭ **LinkVariables**: *object*

*Defined in [src/link.ts:182](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L182)*

A key->value map of variables to place in a templated link

#### Type declaration:

* \[ **key**: *string*\]: string | number

___

###  NewLink

Ƭ **NewLink**: *Omit‹[Link](_src_link_.md#link), "context"›*

*Defined in [src/link.ts:54](https://github.com/evert/ketting/blob/f7a0a1b/src/link.ts#L54)*
