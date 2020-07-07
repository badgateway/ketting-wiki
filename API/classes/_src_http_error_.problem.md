[ketting](../README.md) › [Globals](../globals.md) › ["src/http/error"](../modules/_src_http_error_.md) › [Problem](_src_http_error_.problem.md)

# Class: Problem

Problem extends the HttpError object. If a server emits a HTTP error, and
the response body's content-type is application/problem+json.

application/problem+json is defined in RFC7807 and provides a standardized
way to describe error conditions by a HTTP server.

## Hierarchy

  ↳ [HttpError](_src_http_error_.httperror.md)

  ↳ **Problem**

## Index

### Constructors

* [constructor](_src_http_error_.problem.md#constructor)

### Properties

* [body](_src_http_error_.problem.md#body)
* [message](_src_http_error_.problem.md#message)
* [name](_src_http_error_.problem.md#name)
* [response](_src_http_error_.problem.md#response)
* [stack](_src_http_error_.problem.md#optional-stack)
* [status](_src_http_error_.problem.md#status)

## Constructors

###  constructor

\+ **new Problem**(`response`: Response, `problemBody`: Record‹string, any›): *[Problem](_src_http_error_.problem.md)*

*Overrides [HttpError](_src_http_error_.httperror.md).[constructor](_src_http_error_.httperror.md#constructor)*

*Defined in [src/http/error.ts:32](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L32)*

**Parameters:**

Name | Type |
------ | ------ |
`response` | Response |
`problemBody` | Record‹string, any› |

**Returns:** *[Problem](_src_http_error_.problem.md)*

## Properties

###  body

• **body**: *object*

*Defined in [src/http/error.ts:30](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L30)*

#### Type declaration:

* **title**? : *undefined | string*

___

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

*Inherited from [HttpError](_src_http_error_.httperror.md).[response](_src_http_error_.httperror.md#response)*

*Defined in [src/http/error.ts:10](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L10)*

___

### `Optional` stack

• **stack**? : *undefined | string*

*Inherited from [LinkNotFound](_src_link_.linknotfound.md).[stack](_src_link_.linknotfound.md#optional-stack)*

Defined in node_modules/typescript/lib/lib.es5.d.ts:975

___

###  status

• **status**: *number*

*Inherited from [HttpError](_src_http_error_.httperror.md).[status](_src_http_error_.httperror.md#status)*

*Defined in [src/http/error.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L11)*
