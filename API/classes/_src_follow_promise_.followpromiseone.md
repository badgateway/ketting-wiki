[ketting](../README.md) › [Globals](../globals.md) › ["src/follow-promise"](../modules/_src_follow_promise_.md) › [FollowPromiseOne](_src_follow_promise_.followpromiseone.md)

# Class: FollowPromiseOne ‹**T**›

The FollowPromise class is what's being returned from follow() functions.

It's 'PromiseLike', which means you can treat it like a Promise, and it
can be awaited. When used as a Promise, it resolves to the Resource object
that was followed.

In addition to being a Promise<Resource> stand-in, it also exposes other
functions, namely:

* `follow()` to allow a user to chain several follow() functions to do
  several 'hops' all at once.
* `followAll()`, allowing a user to call `followAll()` at the end of a
  chain.

## Type parameters

▪ **T**

## Hierarchy

* [FollowPromise](_src_follow_promise_.followpromise.md)‹[Resource](_src_resource_.resource.md)‹T››

  ↳ **FollowPromiseOne**

## Implements

* PromiseLike‹[Resource](_src_resource_.resource.md)‹T››

## Index

### Constructors

* [constructor](_src_follow_promise_.followpromiseone.md#constructor)

### Properties

* [preferPushEnabled](_src_follow_promise_.followpromiseone.md#protected-preferpushenabled)
* [preferTranscludeEnabled](_src_follow_promise_.followpromiseone.md#protected-prefertranscludeenabled)
* [prefetchEnabled](_src_follow_promise_.followpromiseone.md#protected-prefetchenabled)
* [rel](_src_follow_promise_.followpromiseone.md#private-rel)
* [resource](_src_follow_promise_.followpromiseone.md#private-resource)
* [useHeadEnabled](_src_follow_promise_.followpromiseone.md#protected-useheadenabled)
* [variables](_src_follow_promise_.followpromiseone.md#private-optional-variables)

### Methods

* [catch](_src_follow_promise_.followpromiseone.md#catch)
* [fetchLinkedResource](_src_follow_promise_.followpromiseone.md#private-fetchlinkedresource)
* [finally](_src_follow_promise_.followpromiseone.md#finally)
* [follow](_src_follow_promise_.followpromiseone.md#follow)
* [followAll](_src_follow_promise_.followpromiseone.md#followall)
* [preFetch](_src_follow_promise_.followpromiseone.md#prefetch)
* [preferPush](_src_follow_promise_.followpromiseone.md#preferpush)
* [preferTransclude](_src_follow_promise_.followpromiseone.md#prefertransclude)
* [then](_src_follow_promise_.followpromiseone.md#then)
* [useHead](_src_follow_promise_.followpromiseone.md#usehead)

## Constructors

###  constructor

\+ **new FollowPromiseOne**(`resource`: [Resource](_src_resource_.resource.md) | Promise‹[Resource](_src_resource_.resource.md)›, `rel`: string, `variables?`: [LinkVariables](../modules/_src_link_.md#linkvariables)): *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)*

*Overrides [FollowPromise](_src_follow_promise_.followpromise.md).[constructor](_src_follow_promise_.followpromise.md#constructor)*

*Defined in [src/follow-promise.ts:75](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L75)*

**Parameters:**

Name | Type |
------ | ------ |
`resource` | [Resource](_src_resource_.resource.md) &#124; Promise‹[Resource](_src_resource_.resource.md)› |
`rel` | string |
`variables?` | [LinkVariables](../modules/_src_link_.md#linkvariables) |

**Returns:** *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)*

## Properties

### `Protected` preferPushEnabled

• **preferPushEnabled**: *boolean*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[preferPushEnabled](_src_follow_promise_.followpromise.md#protected-preferpushenabled)*

*Defined in [src/follow-promise.ts:12](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L12)*

___

### `Protected` preferTranscludeEnabled

• **preferTranscludeEnabled**: *boolean*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[preferTranscludeEnabled](_src_follow_promise_.followpromise.md#protected-prefertranscludeenabled)*

*Defined in [src/follow-promise.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L13)*

___

### `Protected` prefetchEnabled

• **prefetchEnabled**: *boolean*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[prefetchEnabled](_src_follow_promise_.followpromise.md#protected-prefetchenabled)*

*Defined in [src/follow-promise.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L11)*

___

### `Private` rel

• **rel**: *string*

*Defined in [src/follow-promise.ts:74](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L74)*

___

### `Private` resource

• **resource**: *[Resource](_src_resource_.resource.md) | Promise‹[Resource](_src_resource_.resource.md)›*

*Defined in [src/follow-promise.ts:73](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L73)*

___

### `Protected` useHeadEnabled

• **useHeadEnabled**: *boolean*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[useHeadEnabled](_src_follow_promise_.followpromise.md#protected-useheadenabled)*

*Defined in [src/follow-promise.ts:14](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L14)*

___

### `Private` `Optional` variables

• **variables**? : *[LinkVariables](../modules/_src_link_.md#linkvariables)*

*Defined in [src/follow-promise.ts:75](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L75)*

## Methods

###  catch

▸ **catch**‹**TResult1**, **TResult2**›(`onrejected?`: function | null | undefined): *Promise‹TResult1 | TResult2›*

*Overrides [FollowPromise](_src_follow_promise_.followpromise.md).[catch](_src_follow_promise_.followpromise.md#abstract-catch)*

*Defined in [src/follow-promise.ts:104](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L104)*

This 'catch' function behaves like a Promise catch() function.

**Type parameters:**

▪ **TResult1**

▪ **TResult2**

**Parameters:**

Name | Type |
------ | ------ |
`onrejected?` | function &#124; null &#124; undefined |

**Returns:** *Promise‹TResult1 | TResult2›*

___

### `Private` fetchLinkedResource

▸ **fetchLinkedResource**(): *Promise‹[Resource](_src_resource_.resource.md)‹T››*

*Defined in [src/follow-promise.ts:150](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L150)*

This function does the actual fetching of the linked
resource.

**Returns:** *Promise‹[Resource](_src_resource_.resource.md)‹T››*

___

###  finally

▸ **finally**‹**TResult1**›(`onfinally`: function): *Promise‹TResult1›*

*Defined in [src/follow-promise.ts:113](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L113)*

Implementation of a Promise.finally function

**Type parameters:**

▪ **TResult1**

**Parameters:**

▪ **onfinally**: *function*

▸ (): *TResult1 | PromiseLike‹TResult1›*

**Returns:** *Promise‹TResult1›*

___

###  follow

▸ **follow**‹**TNested**›(`rel`: string, `variables?`: [LinkVariables](../modules/_src_link_.md#linkvariables)): *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)‹TNested›*

*Defined in [src/follow-promise.ts:129](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L129)*

Follow another link immediately after following this link.

This allows you to follow several hops of links in one go.

For example: resource.follow('foo').follow('bar');

**Type parameters:**

▪ **TNested**

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |
`variables?` | [LinkVariables](../modules/_src_link_.md#linkvariables) |

**Returns:** *[FollowPromiseOne](_src_follow_promise_.followpromiseone.md)‹TNested›*

___

###  followAll

▸ **followAll**‹**TNested**›(`rel`: string): *[FollowPromiseMany](_src_follow_promise_.followpromisemany.md)‹TNested›*

*Defined in [src/follow-promise.ts:140](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L140)*

Follows a set of links immediately after following this link.

For example: resource.follow('foo').followAll('item');

**Type parameters:**

▪ **TNested**

**Parameters:**

Name | Type |
------ | ------ |
`rel` | string |

**Returns:** *[FollowPromiseMany](_src_follow_promise_.followpromisemany.md)‹TNested›*

___

###  preFetch

▸ **preFetch**(): *this*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[preFetch](_src_follow_promise_.followpromise.md#prefetch)*

*Defined in [src/follow-promise.ts:23](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L23)*

**Returns:** *this*

___

###  preferPush

▸ **preferPush**(): *this*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[preferPush](_src_follow_promise_.followpromise.md#preferpush)*

*Defined in [src/follow-promise.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L28)*

**Returns:** *this*

___

###  preferTransclude

▸ **preferTransclude**(): *this*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[preferTransclude](_src_follow_promise_.followpromise.md#prefertransclude)*

*Defined in [src/follow-promise.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L33)*

**Returns:** *this*

___

###  then

▸ **then**‹**TResult1**, **TResult2**›(`onfulfilled?`: function | null | undefined, `onrejected?`: function | null | undefined): *Promise‹TResult1 | TResult2›*

*Overrides [FollowPromise](_src_follow_promise_.followpromise.md).[then](_src_follow_promise_.followpromise.md#abstract-then)*

*Defined in [src/follow-promise.ts:92](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L92)*

This 'then' function behaves like a Promise then() function.

This method signature is pretty crazy, but trust that it's pretty much
like any then() method on a promise.

**Type parameters:**

▪ **TResult1**

▪ **TResult2**

**Parameters:**

Name | Type |
------ | ------ |
`onfulfilled?` | function &#124; null &#124; undefined |
`onrejected?` | function &#124; null &#124; undefined |

**Returns:** *Promise‹TResult1 | TResult2›*

___

###  useHead

▸ **useHead**(): *this*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[useHead](_src_follow_promise_.followpromise.md#usehead)*

*Defined in [src/follow-promise.ts:44](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L44)*

Use a HTTP HEAD request to fetch the links.

This is useful when interacting with servers that embed links in Link
Headers.

**Returns:** *this*
