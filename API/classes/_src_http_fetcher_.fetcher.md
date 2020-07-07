[ketting](../README.md) › [Globals](../globals.md) › ["src/http/fetcher"](../modules/_src_http_fetcher_.md) › [Fetcher](_src_http_fetcher_.fetcher.md)

# Class: Fetcher

The fetcher object is responsible for calling fetch()

This is wrapped in an object because we want to support
'fetch middlewares'. These middlewares are similar to server-side
middlewares and can intercept requests and alter requests/responses.

## Hierarchy

* **Fetcher**

## Index

### Properties

* [middlewares](_src_http_fetcher_.fetcher.md#middlewares)

### Methods

* [fetch](_src_http_fetcher_.fetcher.md#fetch)
* [fetchOrThrow](_src_http_fetcher_.fetcher.md#fetchorthrow)
* [getMiddlewaresByOrigin](_src_http_fetcher_.fetcher.md#getmiddlewaresbyorigin)
* [use](_src_http_fetcher_.fetcher.md#use)

## Properties

###  middlewares

• **middlewares**: *[RegExp, [FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware)][]* = []

*Defined in [src/http/fetcher.ts:16](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L16)*

## Methods

###  fetch

▸ **fetch**(`resource`: string | Request, `init?`: RequestInit): *Promise‹Response›*

*Defined in [src/http/fetcher.ts:24](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L24)*

A wrapper for MDN fetch()

This wrapper supports 'fetch middlewares'. It will call them
in sequence.

**Parameters:**

Name | Type |
------ | ------ |
`resource` | string &#124; Request |
`init?` | RequestInit |

**Returns:** *Promise‹Response›*

___

###  fetchOrThrow

▸ **fetchOrThrow**(`resource`: string | Request, `init?`: RequestInit): *Promise‹Response›*

*Defined in [src/http/fetcher.ts:82](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L82)*

Does a HTTP request and throws an exception if the server emitted
a HTTP error.

**`see`** https://developer.mozilla.org/en-US/docs/Web/API/Request/Request

**Parameters:**

Name | Type |
------ | ------ |
`resource` | string &#124; Request |
`init?` | RequestInit |

**Returns:** *Promise‹Response›*

___

###  getMiddlewaresByOrigin

▸ **getMiddlewaresByOrigin**(`origin`: string): *[FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware)[]*

*Defined in [src/http/fetcher.ts:49](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L49)*

Returns the list of middlewares that are applicable to
a specific origin

**Parameters:**

Name | Type |
------ | ------ |
`origin` | string |

**Returns:** *[FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware)[]*

___

###  use

▸ **use**(`mw`: [FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware), `origin`: string): *void*

*Defined in [src/http/fetcher.ts:63](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L63)*

Add a middleware

**Parameters:**

Name | Type | Default |
------ | ------ | ------ |
`mw` | [FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware) | - |
`origin` | string | "*" |

**Returns:** *void*
