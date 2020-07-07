[ketting](../README.md) › [Globals](../globals.md) › ["src/http/error"](_src_http_error_.md)

# Module: "src/http/error"

## Index

### Classes

* [HttpError](../classes/_src_http_error_.httperror.md)
* [Problem](../classes/_src_http_error_.problem.md)

### Functions

* [problemFactory](_src_http_error_.md#problemfactory)

## Functions

###  problemFactory

▸ **problemFactory**(`response`: Response): *Promise‹[HttpError](../classes/_src_http_error_.httperror.md) | [Problem](../classes/_src_http_error_.problem.md)›*

*Defined in [src/http/error.ts:54](https://github.com/evert/ketting/blob/f7a0a1b/src/http/error.ts#L54)*

This function creates problems, not unlike the the author of this file.

It takes a Fetch Response object, and returns a HttpError. If the HTTP
response has a type of application/problem+json it will return a Problem
object.

Because parsing the response might be asynchronous, the function returns
a Promise resolving in either object.

**Parameters:**

Name | Type |
------ | ------ |
`response` | Response |

**Returns:** *Promise‹[HttpError](../classes/_src_http_error_.httperror.md) | [Problem](../classes/_src_http_error_.problem.md)›*
