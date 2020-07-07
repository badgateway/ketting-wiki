[ketting](../README.md) › [Globals](../globals.md) › ["src/http/error"](../modules/_src_http_error_.md) › [HttpError](_src_http_error_.httperror.md)

# Class: HttpError

HttpError extends the Error object, and is thrown wheenever servers emit
HTTP errors.

It has a response property, allowing users to find out more about the
nature of the error.

## Hierarchy

* [Error](_src_link_.linknotfound.md#static-error)

  ↳ **HttpError**

  ↳ [Problem](_src_http_error_.problem.md)

## Index

### Constructors

* [constructor](_src_http_error_.httperror.md#constructor)

### Properties

* [message](_src_http_error_.httperror.md#message)
* [name](_src_http_error_.httperror.md#name)
* [response](_src_http_error_.httperror.md#response)
* [stack](_src_http_error_.httperror.md#optional-stack)
* [status](_src_http_error_.httperror.md#status)
* [Error](_src_http_error_.httperror.md#static-error)

## Constructors

###  constructor

\+ **new HttpError**(`response`: Response): *[HttpError](_src_http_error_.httperror.md)*

*Defined in [src/http/error.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L11)*

**Parameters:**

Name | Type |
------ | ------ |
`response` | Response |

**Returns:** *[HttpError](_src_http_error_.httperror.md)*

## Properties

###  message

• **message**: *string*

*Inherited from [LinkNotFound](_src_link_.linknotfound.md).[message](_src_link_.linknotfound.md#message)*

Defined in node_modules/typescript/lib/lib.es5.d.ts:974

___

###  name

• **name**: *string*

*Inherited from [LinkNotFound](_src_link_.linknotfound.md).[name](_src_link_.linknotfound.md#name)*

Defined in node_modules/typescript/lib/lib.es5.d.ts:973

___

###  response

• **response**: *Response*

*Defined in [src/http/error.ts:10](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L10)*

___

### `Optional` stack

• **stack**? : *undefined | string*

*Inherited from [LinkNotFound](_src_link_.linknotfound.md).[stack](_src_link_.linknotfound.md#optional-stack)*

*Overrides [LinkNotFound](_src_link_.linknotfound.md).[stack](_src_link_.linknotfound.md#optional-stack)*

Defined in node_modules/typescript/lib/lib.es5.d.ts:975

___

###  status

• **status**: *number*

*Defined in [src/http/error.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L11)*

___

### `Static` Error

▪ **Error**: *ErrorConstructor*

Defined in node_modules/typescript/lib/lib.es5.d.ts:984
