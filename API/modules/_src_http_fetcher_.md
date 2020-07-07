[ketting](../README.md) › [Globals](../globals.md) › ["src/http/fetcher"](_src_http_fetcher_.md)

# Module: "src/http/fetcher"

## Index

### Classes

* [Fetcher](../classes/_src_http_fetcher_.fetcher.md)

### Type aliases

* [FetchMiddleware](_src_http_fetcher_.md#fetchmiddleware)

### Functions

* [invokeMiddlewares](_src_http_fetcher_.md#invokemiddlewares)

## Type aliases

###  FetchMiddleware

Ƭ **FetchMiddleware**: *function*

*Defined in [src/http/fetcher.ts:4](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L4)*

#### Type declaration:

▸ (`request`: Request, `next`: function): *Promise‹Response›*

**Parameters:**

▪ **request**: *Request*

▪ **next**: *function*

▸ (`request`: Request): *Promise‹Response›*

**Parameters:**

Name | Type |
------ | ------ |
`request` | Request |

## Functions

###  invokeMiddlewares

▸ **invokeMiddlewares**(`mws`: [FetchMiddleware](_src_http_fetcher_.md#fetchmiddleware)[], `request`: Request): *Promise‹Response›*

*Defined in [src/http/fetcher.ts:97](https://github.com/evert/ketting/blob/f7a0a1b/src/http/fetcher.ts#L97)*

**Parameters:**

Name | Type |
------ | ------ |
`mws` | [FetchMiddleware](_src_http_fetcher_.md#fetchmiddleware)[] |
`request` | Request |

**Returns:** *Promise‹Response›*
