[ketting](../README.md) › [Globals](../globals.md) › ["src/resource"](../modules/_src_resource_.md) › [Resource](_src_resource_.resource.md)

# Class: Resource ‹**T, T**›

A 'resource' represents an endpoint on the server.

The endpoint has a uri, you might for example be able to GET its
presentation.

A resource may also have a list of links on them, pointing to other
resources.

## Type parameters

▪ **T**

▪ **T**

## Hierarchy

* EventEmitter

  ↳ **Resource**

## Index

### Constructors

* [constructor](_src_resource_.resource.md#constructor)

### Properties

* [activeRefresh](_src_resource_.resource.md#activerefresh)
* [client](_src_resource_.resource.md#client)
* [uri](_src_resource_.resource.md#uri)
* [defaultMaxListeners](_src_resource_.resource.md#static-defaultmaxlisteners)

### Methods

* [addListener](_src_resource_.resource.md#addlistener)
* [clearCache](_src_resource_.resource.md#clearcache)
* [delete](_src_resource_.resource.md#delete)
* [emit](_src_resource_.resource.md#emit)
* [eventNames](_src_resource_.resource.md#eventnames)
* [fetch](_src_resource_.resource.md#fetch)
* [fetchOrThrow](_src_resource_.resource.md#fetchorthrow)
* [follow](_src_resource_.resource.md#follow)
* [followAll](_src_resource_.resource.md#followall)
* [get](_src_resource_.resource.md#get)
* [getMaxListeners](_src_resource_.resource.md#getmaxlisteners)
* [go](_src_resource_.resource.md#go)
* [hasLink](_src_resource_.resource.md#haslink)
* [head](_src_resource_.resource.md#head)
* [link](_src_resource_.resource.md#link)
* [links](_src_resource_.resource.md#links)
* [listenerCount](_src_resource_.resource.md#listenercount)
* [listeners](_src_resource_.resource.md#listeners)
* [off](_src_resource_.resource.md#off)
* [on](_src_resource_.resource.md#on)
* [once](_src_resource_.resource.md#once)
* [patch](_src_resource_.resource.md#patch)
* [post](_src_resource_.resource.md#post)
* [postFollow](_src_resource_.resource.md#postfollow)
* [prependListener](_src_resource_.resource.md#prependlistener)
* [prependOnceListener](_src_resource_.resource.md#prependoncelistener)
* [put](_src_resource_.resource.md#put)
* [rawListeners](_src_resource_.resource.md#rawlisteners)
* [refresh](_src_resource_.resource.md#refresh)
* [removeAllListeners](_src_resource_.resource.md#removealllisteners)
* [removeListener](_src_resource_.resource.md#removelistener)
* [setMaxListeners](_src_resource_.resource.md#setmaxlisteners)
* [updateCache](_src_resource_.resource.md#updatecache)
* [listenerCount](_src_resource_.resource.md#static-listenercount)

## Constructors

###  constructor

\+ **new Resource**(`client`: [Client](_src_client_.client.md), `uri`: string): *[Resource](_src_resource_.resource.md)*

*Defined in [src/resource.ts:24](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L24)*

uri must be absolute

**Parameters:**

Name | Type |
------ | ------ |
`client` | [Client](_src_client_.client.md) |
`uri` | string |

**Returns:** *[Resource](_src_resource_.resource.md)*

## Properties

###  activeRefresh

• **activeRefresh**: *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹T›› | null*

*Defined in [src/resource.ts:24](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L24)*

___

###  client

• **client**: *[Client](_src_client_.client.md)*

*Defined in [src/resource.ts:22](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L22)*

___

###  uri

• **uri**: *string*

*Defined in [src/resource.ts:21](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L21)*

___

### `Static` defaultMaxListeners

▪ **defaultMaxListeners**: *number*

*Inherited from [Resource](_src_resource_.resource.md).[defaultMaxListeners](_src_resource_.resource.md#static-defaultmaxlisteners)*

Defined in node_modules/@types/node/events.d.ts:18

## Methods

###  addListener

▸ **addListener**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[addListener](_src_resource_.resource.md#addlistener)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:20

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

___

###  clearCache

▸ **clearCache**(): *void*

*Defined in [src/resource.ts:282](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L282)*

Clears the state cache for this resource.

**Returns:** *void*

___

###  delete

▸ **delete**(): *Promise‹void›*

*Defined in [src/resource.ts:137](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L137)*

Deletes the resource

**Returns:** *Promise‹void›*

___

###  emit

▸ **emit**(`event`: string | symbol, ...`args`: any[]): *boolean*

*Inherited from [Resource](_src_resource_.resource.md).[emit](_src_resource_.resource.md#emit)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:32

**Parameters:**

Name | Type |
------ | ------ |
`event` | string &#124; symbol |
`...args` | any[] |

**Returns:** *boolean*

▸ **emit**(`event`: "update", `state`: [State](../interfaces/_src_state_interface_.state.md)): *boolean*

*Inherited from [Resource](_src_resource_.resource.md).[emit](_src_resource_.resource.md#emit)*

*Defined in [src/resource.ts:352](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L352)*

**Parameters:**

Name | Type |
------ | ------ |
`event` | "update" |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *boolean*

▸ **emit**(`event`: "stale"): *boolean*

*Inherited from [Resource](_src_resource_.resource.md).[emit](_src_resource_.resource.md#emit)*

*Defined in [src/resource.ts:353](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L353)*

**Parameters:**

Name | Type |
------ | ------ |
`event` | "stale" |

**Returns:** *boolean*

▸ **emit**(`event`: "delete"): *boolean*

*Inherited from [Resource](_src_resource_.resource.md).[emit](_src_resource_.resource.md#emit)*

*Defined in [src/resource.ts:354](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L354)*

**Parameters:**

Name | Type |
------ | ------ |
`event` | "delete" |

**Returns:** *boolean*

___

###  eventNames

▸ **eventNames**(): *Array‹string | symbol›*

*Inherited from [Resource](_src_resource_.resource.md).[eventNames](_src_resource_.resource.md#eventnames)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:33

**Returns:** *Array‹string | symbol›*

___

###  fetch

▸ **fetch**(`init?`: RequestInit): *Promise‹Response›*

*Defined in [src/resource.ts:249](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L249)*

Does a HTTP request on the current resource URI

**Parameters:**

Name | Type |
------ | ------ |
`init?` | RequestInit |

**Returns:** *Promise‹Response›*

___

###  fetchOrThrow

▸ **fetchOrThrow**(`init?`: RequestInit): *Promise‹Response›*

*Defined in [src/resource.ts:261](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L261)*

Does a HTTP request on the current resource URI.

If the response was a 4XX or 5XX, this function will throw
an exception.

**Parameters:**

Name | Type |
------ | ------ |
`init?` | RequestInit |

**Returns:** *Promise‹Response›*

___

###  follow

▸ **follow**‹**TFollowedResource**›(`rel`: string, `variables?`: [LinkVariables](../modules/_src_link_.md#linkvariables)): *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)‹TFollowedResource›*

*Defined in [src/resource.ts:213](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L213)*

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

###  followAll

▸ **followAll**‹**TFollowedResource**›(`rel`: string): *[FollowPromiseMany](_src_follow_promise_.followpromisemany.md)‹TFollowedResource›*

*Defined in [src/resource.ts:225](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L225)*

Follows a relationship based on its reltype. This function returns a
Promise that resolves to an array of Resource objects.

If no resources were found, the array will be empty.

**Type parameters:**

▪ **TFollowedResource**

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *[FollowPromiseMany](_src_follow_promise_.followpromisemany.md)‹TFollowedResource›*

___

###  get

▸ **get**(`getOptions?`: [GetRequestOptions](../modules/_src_types_.md#getrequestoptions)): *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹T››*

*Defined in [src/resource.ts:42](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L42)*

Gets the current state of the resource.

This function will return a State object.

**Parameters:**

Name | Type |
------ | ------ |
`getOptions?` | [GetRequestOptions](../modules/_src_types_.md#getrequestoptions) |

**Returns:** *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹T››*

___

###  getMaxListeners

▸ **getMaxListeners**(): *number*

*Inherited from [Resource](_src_resource_.resource.md).[getMaxListeners](_src_resource_.resource.md#getmaxlisteners)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:29

**Returns:** *number*

___

###  go

▸ **go**‹**TGoResource**›(`uri`: string): *[Resource](_src_resource_.resource.md)‹TGoResource›*

*Defined in [src/resource.ts:239](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L239)*

Resolves a new resource based on a relative uri.

Use this function to manually get a Resource object via a uri. The uri
will be resolved based on the uri of the current resource.

This function doesn't do any HTTP requests.

**Type parameters:**

▪ **TGoResource**

**Parameters:**

Name | Type |
------ | ------ |
`uri` | string |

**Returns:** *[Resource](_src_resource_.resource.md)‹TGoResource›*

___

###  hasLink

▸ **hasLink**(`rel`: string): *Promise‹boolean›*

*Defined in [src/resource.ts:330](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L330)*

Returns true or false depending on if a link with the specified relation
type exists.

**`deprecated`** 

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *Promise‹boolean›*

___

###  head

▸ **head**(`headOptions?`: [HeadRequestOptions](../modules/_src_types_.md#headrequestoptions)): *Promise‹[HeadState](../interfaces/_src_state_interface_.headstate.md)›*

*Defined in [src/resource.ts:58](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L58)*

Does a HEAD request and returns a HeadState object.

If there was a valid existing cache for a GET request, it will
still return that.

**Parameters:**

Name | Type |
------ | ------ |
`headOptions?` | [HeadRequestOptions](../modules/_src_types_.md#headrequestoptions) |

**Returns:** *Promise‹[HeadState](../interfaces/_src_state_interface_.headstate.md)›*

___

###  link

▸ **link**(`rel`: string): *Promise‹[Link](../modules/_src_link_.md#link)›*

*Defined in [src/resource.ts:295](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L295)*

Returns a Link object, by its REL.

If the link does not exist, a LinkNotFound error will be thrown.

**`deprecated`** 

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *Promise‹[Link](../modules/_src_link_.md#link)›*

___

###  links

▸ **links**(`rel?`: undefined | string): *Promise‹[Link](../modules/_src_link_.md#link)[]›*

*Defined in [src/resource.ts:312](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L312)*

Returns all links defined on this object.

**`deprecated`** 

**Parameters:**

Name | Type |
------ | ------ |
`rel?` | undefined &#124; string |

**Returns:** *Promise‹[Link](../modules/_src_link_.md#link)[]›*

___

###  listenerCount

▸ **listenerCount**(`type`: string | symbol): *number*

*Inherited from [Resource](_src_resource_.resource.md).[listenerCount](_src_resource_.resource.md#static-listenercount)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:34

**Parameters:**

Name | Type |
------ | ------ |
`type` | string &#124; symbol |

**Returns:** *number*

___

###  listeners

▸ **listeners**(`event`: string | symbol): *Function[]*

*Inherited from [Resource](_src_resource_.resource.md).[listeners](_src_resource_.resource.md#listeners)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:30

**Parameters:**

Name | Type |
------ | ------ |
`event` | string &#124; symbol |

**Returns:** *Function[]*

___

###  off

▸ **off**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[off](_src_resource_.resource.md#off)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:26

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

▸ **off**(`event`: "update", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[off](_src_resource_.resource.md#off)*

*Defined in [src/resource.ts:348](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L348)*

**Parameters:**

▪ **event**: *"update"*

▪ **listener**: *function*

▸ (`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *this*

▸ **off**(`event`: "stale", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[off](_src_resource_.resource.md#off)*

*Defined in [src/resource.ts:349](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L349)*

**Parameters:**

▪ **event**: *"stale"*

▪ **listener**: *function*

▸ (): *void*

**Returns:** *this*

▸ **off**(`event`: "delete", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[off](_src_resource_.resource.md#off)*

*Defined in [src/resource.ts:350](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L350)*

**Parameters:**

▪ **event**: *"delete"*

▪ **listener**: *function*

▸ (): *void*

**Returns:** *this*

___

###  on

▸ **on**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[on](_src_resource_.resource.md#on)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:21

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

▸ **on**(`event`: "update", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[on](_src_resource_.resource.md#on)*

*Defined in [src/resource.ts:340](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L340)*

**Parameters:**

▪ **event**: *"update"*

▪ **listener**: *function*

▸ (`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *this*

▸ **on**(`event`: "stale", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[on](_src_resource_.resource.md#on)*

*Defined in [src/resource.ts:341](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L341)*

**Parameters:**

▪ **event**: *"stale"*

▪ **listener**: *function*

▸ (): *void*

**Returns:** *this*

▸ **on**(`event`: "delete", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[on](_src_resource_.resource.md#on)*

*Defined in [src/resource.ts:342](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L342)*

**Parameters:**

▪ **event**: *"delete"*

▪ **listener**: *function*

▸ (): *void*

**Returns:** *this*

___

###  once

▸ **once**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[once](_src_resource_.resource.md#once)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:22

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

▸ **once**(`event`: "update", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[once](_src_resource_.resource.md#once)*

*Defined in [src/resource.ts:344](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L344)*

**Parameters:**

▪ **event**: *"update"*

▪ **listener**: *function*

▸ (`state`: [State](../interfaces/_src_state_interface_.state.md)): *void*

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *this*

▸ **once**(`event`: "stale", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[once](_src_resource_.resource.md#once)*

*Defined in [src/resource.ts:345](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L345)*

**Parameters:**

▪ **event**: *"stale"*

▪ **listener**: *function*

▸ (): *void*

**Returns:** *this*

▸ **once**(`event`: "delete", `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[once](_src_resource_.resource.md#once)*

*Defined in [src/resource.ts:346](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L346)*

**Parameters:**

▪ **event**: *"delete"*

▪ **listener**: *function*

▸ (): *void*

**Returns:** *this*

___

###  patch

▸ **patch**(`options`: [PatchRequestOptions](../modules/_src_types_.md#patchrequestoptions)): *Promise‹void›*

*Defined in [src/resource.ts:198](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L198)*

Sends a PATCH request to the resource.

This function defaults to a application/json content-type header.

**Parameters:**

Name | Type |
------ | ------ |
`options` | [PatchRequestOptions](../modules/_src_types_.md#patchrequestoptions) |

**Returns:** *Promise‹void›*

___

###  post

▸ **post**(`options`: [PostRequestOptions](../modules/_src_types_.md#postrequestoptions)): *Promise‹[State](../interfaces/_src_state_interface_.state.md)›*

*Defined in [src/resource.ts:153](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L153)*

Sends a POST request to the resource.

See the documentation for PostRequestOptions for more details.
This function is used for RPC-like endpoints and form submissions.

This function will return the response as a State object.

**Parameters:**

Name | Type |
------ | ------ |
`options` | [PostRequestOptions](../modules/_src_types_.md#postrequestoptions) |

**Returns:** *Promise‹[State](../interfaces/_src_state_interface_.state.md)›*

___

###  postFollow

▸ **postFollow**(`options`: [PostRequestOptions](../modules/_src_types_.md#postrequestoptions)): *Promise‹[Resource](_src_resource_.resource.md)›*

*Defined in [src/resource.ts:172](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L172)*

Sends a POST request, and follows to the next resource.

If a server responds with a 201 Status code and a Location header,
it will automatically return the newly created resource.

If the server responded with a 204 or 205, this function will return
`this`.

**Parameters:**

Name | Type |
------ | ------ |
`options` | [PostRequestOptions](../modules/_src_types_.md#postrequestoptions) |

**Returns:** *Promise‹[Resource](_src_resource_.resource.md)›*

___

###  prependListener

▸ **prependListener**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[prependListener](_src_resource_.resource.md#prependlistener)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:23

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

___

###  prependOnceListener

▸ **prependOnceListener**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[prependOnceListener](_src_resource_.resource.md#prependoncelistener)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:24

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

___

###  put

▸ **put**(`options`: [PutRequestOptions](../modules/_src_types_.md#putrequestoptions)‹T› | [State](../interfaces/_src_state_interface_.state.md)): *Promise‹void›*

*Defined in [src/resource.ts:109](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L109)*

Updates the server state with a PUT request

**Parameters:**

Name | Type |
------ | ------ |
`options` | [PutRequestOptions](../modules/_src_types_.md#putrequestoptions)‹T› &#124; [State](../interfaces/_src_state_interface_.state.md) |

**Returns:** *Promise‹void›*

___

###  rawListeners

▸ **rawListeners**(`event`: string | symbol): *Function[]*

*Inherited from [Resource](_src_resource_.resource.md).[rawListeners](_src_resource_.resource.md#rawlisteners)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:31

**Parameters:**

Name | Type |
------ | ------ |
`event` | string &#124; symbol |

**Returns:** *Function[]*

___

###  refresh

▸ **refresh**(`getOptions?`: [GetRequestOptions](../modules/_src_types_.md#getrequestoptions)): *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹T››*

*Defined in [src/resource.ts:81](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L81)*

Gets the current state of the resource, skipping
the cache.

This function will return a State object.

**Parameters:**

Name | Type |
------ | ------ |
`getOptions?` | [GetRequestOptions](../modules/_src_types_.md#getrequestoptions) |

**Returns:** *Promise‹[State](../interfaces/_src_state_interface_.state.md)‹T››*

___

###  removeAllListeners

▸ **removeAllListeners**(`event?`: string | symbol): *this*

*Inherited from [Resource](_src_resource_.resource.md).[removeAllListeners](_src_resource_.resource.md#removealllisteners)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:27

**Parameters:**

Name | Type |
------ | ------ |
`event?` | string &#124; symbol |

**Returns:** *this*

___

###  removeListener

▸ **removeListener**(`event`: string | symbol, `listener`: function): *this*

*Inherited from [Resource](_src_resource_.resource.md).[removeListener](_src_resource_.resource.md#removelistener)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:25

**Parameters:**

▪ **event**: *string | symbol*

▪ **listener**: *function*

▸ (...`args`: any[]): *void*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any[] |

**Returns:** *this*

___

###  setMaxListeners

▸ **setMaxListeners**(`n`: number): *this*

*Inherited from [Resource](_src_resource_.resource.md).[setMaxListeners](_src_resource_.resource.md#setmaxlisteners)*

*Overrides void*

Defined in node_modules/@types/node/events.d.ts:28

**Parameters:**

Name | Type |
------ | ------ |
`n` | number |

**Returns:** *this*

___

###  updateCache

▸ **updateCache**(`state`: [State](../interfaces/_src_state_interface_.state.md)‹T›): *void*

*Defined in [src/resource.ts:272](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L272)*

Updates the state cache, and emits events.

This will update the local state but *not* update the server

**Parameters:**

Name | Type |
------ | ------ |
`state` | [State](../interfaces/_src_state_interface_.state.md)‹T› |

**Returns:** *void*

___

### `Static` listenerCount

▸ **listenerCount**(`emitter`: EventEmitter, `event`: string | symbol): *number*

*Inherited from [Resource](_src_resource_.resource.md).[listenerCount](_src_resource_.resource.md#static-listenercount)*

Defined in node_modules/@types/node/events.d.ts:17

**`deprecated`** since v4.0.0

**Parameters:**

Name | Type |
------ | ------ |
`emitter` | EventEmitter |
`event` | string &#124; symbol |

**Returns:** *number*
