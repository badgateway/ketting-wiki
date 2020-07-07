[ketting](../README.md) › [Globals](../globals.md) › ["src/follow-promise"](../modules/_src_follow_promise_.md) › [FollowPromiseMany](_src_follow_promise_.followpromisemany.md)

# Class: FollowPromiseMany ‹**T**›

## Type parameters

▪ **T**

## Hierarchy

* [FollowPromise](_src_follow_promise_.followpromise.md)‹[Resource](_src_resource_.resource.md)‹T›[]›

  ↳ **FollowPromiseMany**

## Implements

* PromiseLike‹[Resource](_src_resource_.resource.md)‹T›[]›

## Index

### Constructors

* [constructor](_src_follow_promise_.followpromisemany.md#constructor)

### Properties

* [preferPushEnabled](_src_follow_promise_.followpromisemany.md#protected-preferpushenabled)
* [preferTranscludeEnabled](_src_follow_promise_.followpromisemany.md#protected-prefertranscludeenabled)
* [prefetchEnabled](_src_follow_promise_.followpromisemany.md#protected-prefetchenabled)
* [rel](_src_follow_promise_.followpromisemany.md#private-rel)
* [resource](_src_follow_promise_.followpromisemany.md#private-resource)
* [useHeadEnabled](_src_follow_promise_.followpromisemany.md#protected-useheadenabled)

### Methods

* [catch](_src_follow_promise_.followpromisemany.md#catch)
* [fetchLinkedResources](_src_follow_promise_.followpromisemany.md#private-fetchlinkedresources)
* [finally](_src_follow_promise_.followpromisemany.md#finally)
* [preFetch](_src_follow_promise_.followpromisemany.md#prefetch)
* [preferPush](_src_follow_promise_.followpromisemany.md#preferpush)
* [preferTransclude](_src_follow_promise_.followpromisemany.md#prefertransclude)
* [then](_src_follow_promise_.followpromisemany.md#then)
* [useHead](_src_follow_promise_.followpromisemany.md#usehead)

## Constructors

###  constructor

\+ **new FollowPromiseMany**(`resource`: [Resource](_src_resource_.resource.md) | Promise‹[Resource](_src_resource_.resource.md)›, `rel`: string): *[FollowPromiseMany](_src_follow_promise_.followpromisemany.md)*

*Overrides [FollowPromise](_src_follow_promise_.followpromise.md).[constructor](_src_follow_promise_.followpromise.md#constructor)*

*Defined in [src/follow-promise.ts:202](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L202)*

**Parameters:**

Name | Type |
------ | ------ |
`resource` | [Resource](_src_resource_.resource.md) &#124; Promise‹[Resource](_src_resource_.resource.md)› |
`rel` | string |

**Returns:** *[FollowPromiseMany](_src_follow_promise_.followpromisemany.md)*

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

*Defined in [src/follow-promise.ts:202](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L202)*

___

### `Private` resource

• **resource**: *[Resource](_src_resource_.resource.md) | Promise‹[Resource](_src_resource_.resource.md)›*

*Defined in [src/follow-promise.ts:201](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L201)*

___

### `Protected` useHeadEnabled

• **useHeadEnabled**: *boolean*

*Inherited from [FollowPromise](_src_follow_promise_.followpromise.md).[useHeadEnabled](_src_follow_promise_.followpromise.md#protected-useheadenabled)*

*Defined in [src/follow-promise.ts:14](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L14)*

## Methods

###  catch

▸ **catch**‹**TResult1**, **TResult2**›(`onrejected?`: function | null | undefined): *Promise‹TResult1 | TResult2›*

*Overrides [FollowPromise](_src_follow_promise_.followpromise.md).[catch](_src_follow_promise_.followpromise.md#abstract-catch)*

*Defined in [src/follow-promise.ts:227](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L227)*

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

### `Private` fetchLinkedResources

▸ **fetchLinkedResources**(): *Promise‹[Resource](_src_resource_.resource.md)‹T›[]›*

*Defined in [src/follow-promise.ts:249](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L249)*

This function does the actual fetching, to obtained the url
of the linked resource. It returns the Resource object.

**Returns:** *Promise‹[Resource](_src_resource_.resource.md)‹T›[]›*

___

###  finally

▸ **finally**‹**TResult1**›(`onfinally`: function): *Promise‹TResult1›*

*Defined in [src/follow-promise.ts:236](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L236)*

Implementation of a Promise.finally function

**Type parameters:**

▪ **TResult1**

**Parameters:**

▪ **onfinally**: *function*

▸ (): *TResult1 | PromiseLike‹TResult1›*

**Returns:** *Promise‹TResult1›*

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

*Defined in [src/follow-promise.ts:215](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L215)*

This 'then' function behaves like a Promise then() function.

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
