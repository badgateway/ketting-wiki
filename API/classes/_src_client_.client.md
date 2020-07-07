[ketting](../README.md) › [Globals](../globals.md) › ["src/client"](../modules/_src_client_.md) › [Client](_src_client_.client.md)

# Class: Client

## Hierarchy

* **Client**

## Index

### Constructors

* [constructor](_src_client_.client.md#constructor)

### Properties

* [bookmarkUri](_src_client_.client.md#bookmarkuri)
* [cache](_src_client_.client.md#cache)
* [fetcher](_src_client_.client.md#fetcher)
* [resources](_src_client_.client.md#resources)

### Methods

* [acceptHeader](_src_client_.client.md#private-acceptheader)
* [cacheExpireHandler](_src_client_.client.md#private-cacheexpirehandler)
* [cacheState](_src_client_.client.md#cachestate)
* [clearCache](_src_client_.client.md#clearcache)
* [follow](_src_client_.client.md#follow)
* [getStateForResponse](_src_client_.client.md#getstateforresponse)
* [go](_src_client_.client.md#go)
* [use](_src_client_.client.md#use)

### Object literals

* [contentTypeMap](_src_client_.client.md#contenttypemap)

## Constructors

###  constructor

\+ **new Client**(`bookmarkUri`: string): *[Client](_src_client_.client.md)*

*Defined in [src/client.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L38)*

**Parameters:**

Name | Type |
------ | ------ |
`bookmarkUri` | string |

**Returns:** *[Client](_src_client_.client.md)*

## Properties

###  bookmarkUri

• **bookmarkUri**: *string*

*Defined in [src/client.ts:23](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L23)*

___

###  cache

• **cache**: *[StateCache](../interfaces/_src_cache_index_.statecache.md)*

*Defined in [src/client.ts:36](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L36)*

___

###  fetcher

• **fetcher**: *[Fetcher](_src_http_fetcher_.fetcher.md)*

*Defined in [src/client.ts:22](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L22)*

___

###  resources

• **resources**: *Map‹string, [Resource](_src_resource_.resource.md)›*

*Defined in [src/client.ts:38](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L38)*

## Methods

### `Private` acceptHeader

▸ **acceptHeader**(`request`: Request, `next`: function): *Promise‹Response›*

*Defined in [src/client.ts:158](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L158)*

**Parameters:**

▪ **request**: *Request*

▪ **next**: *function*

▸ (`request`: Request): *Promise‹Response›*

**Parameters:**

Name | Type |
------ | ------ |
`request` | Request |

**Returns:** *Promise‹Response›*

___

### `Private` cacheExpireHandler

▸ **cacheExpireHandler**(`request`: Request, `next`: function): *Promise‹Response›*

*Defined in [src/client.ts:170](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L170)*

**Parameters:**

▪ **request**: *Request*

▪ **next**: *function*

▸ (`request`: Request): *Promise‹Response›*

**Parameters:**

Name | Type |
------ | ------ |
`request` | Request |

**Returns:** *Promise‹Response›*

___

###  cacheState

▸ **cacheState**(`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

*Defined in [src/client.ts:142](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L142)*

Caches a State object

This function will also emit 'update' events to resources, and store all
embedded states.

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *void*

___

###  clearCache

▸ **clearCache**(): *void*

*Defined in [src/client.ts:104](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L104)*

Clears the entire resource cache

**Returns:** *void*

___

###  follow

▸ **follow**‹**TFollowedResource**›(`rel`: string, `variables?`: [LinkVariables](../modules/_src_link_.md#linkvariables)): *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)‹TFollowedResource›*

*Defined in [src/client.ts:56](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L56)*

Follows a relationship, based on its reltype. For example, this might be
'alternate', 'item', 'edit' or a custom url-based one.

This function can also follow templated uris. You can specify uri
variables in the optional variables argument.

**Type parameters:**

▪ **TFollowedResource**

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |
`variables?` | [LinkVariables](../modules/_src_link_.md#linkvariables) |

**Returns:** *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)‹TFollowedResource›*

___

###  getStateForResponse

▸ **getStateForResponse**(`uri`: string, `response`: Response): *Promise‹[State](../interfaces/_src_state_interface_.state.md)›*

*Defined in [src/client.ts:113](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L113)*

Transforms a fetch Response to a State object.

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |
`response` | Response |

**Returns:** *Promise‹[State](../interfaces/_src_state_interface_.state.md)›*

___

###  go

▸ **go**‹**TResource**›(`uri?`: undefined | string): *[Resource](_src_resource_.resource.md)‹TResource›*

*Defined in [src/client.ts:78](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L78)*

Returns a resource by its uri.

This function doesn't do any HTTP requests. The uri is optional. If it's
not specified, it will return the bookmark resource.

If a relative uri is passed, it will be resolved based on the bookmark
uri.

**`example`** 
const res = ketting.go('https://example.org/);

**`example`** 
const res = ketting.go<Author>('/users/1');

**`example`** 
const res = ketting.go(); // bookmark

**Type parameters:**

▪ **TResource**

**Parameters:**

Name | Type |
------ | ------ |
`uri?` | undefined &#124; string |

**Returns:** *[Resource](_src_resource_.resource.md)‹TResource›*

___

###  use

▸ **use**(`middleware`: [FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware), `origin`: string): *void*

*Defined in [src/client.ts:95](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L95)*

**Parameters:**

Name | Type | Default |
------ | ------ | ------ |
`middleware` | [FetchMiddleware](../modules/_src_http_fetcher_.md#fetchmiddleware) | - |
`origin` | string | "*" |

**Returns:** *void*

## Object literals

###  contentTypeMap

### ▪ **contentTypeMap**: *object*

*Defined in [src/client.ts:25](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L25)*

###  application/hal+json

• **application/hal+json**: *[factory, string]* = [halStateFactory, '1.0']

*Defined in [src/client.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L28)*

###  application/json

• **application/json**: *[factory, string]* = [halStateFactory, '0.8']

*Defined in [src/client.ts:32](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L32)*

###  application/vnd.api+json

• **application/vnd.api+json**: *[factory, string]* = [jsonApiStateFactory, '0.9']

*Defined in [src/client.ts:29](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L29)*

###  application/vnd.collection+json

• **application/vnd.collection+json**: *[factory, string]* = [cjStateFactory, '0.9']

*Defined in [src/client.ts:31](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L31)*

###  application/vnd.siren+json

• **application/vnd.siren+json**: *[factory, string]* = [sirenStateFactory, '0.9']

*Defined in [src/client.ts:30](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L30)*

###  text/html

• **text/html**: *[factory, string]* = [htmlStateFactory, '0.7']

*Defined in [src/client.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/client.ts#L33)*
