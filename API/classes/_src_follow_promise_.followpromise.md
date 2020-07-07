[ketting](../README.md) › [Globals](../globals.md) › ["src/follow-promise"](../modules/_src_follow_promise_.md) › [FollowPromise](_src_follow_promise_.followpromise.md)

# Class: FollowPromise ‹**T**›

Base interface for both FollowOne and FollowAll

## Type parameters

▪ **T**

## Hierarchy

* **FollowPromise**

  ↳ [FollowPromiseOne](_src_follow_promise_.followpromiseone.md)

  ↳ [FollowPromiseMany](_src_follow_promise_.followpromisemany.md)

## Implements

* PromiseLike‹T›

## Index

### Constructors

* [constructor](_src_follow_promise_.followpromise.md#constructor)

### Properties

* [preferPushEnabled](_src_follow_promise_.followpromise.md#protected-preferpushenabled)
* [preferTranscludeEnabled](_src_follow_promise_.followpromise.md#protected-prefertranscludeenabled)
* [prefetchEnabled](_src_follow_promise_.followpromise.md#protected-prefetchenabled)
* [useHeadEnabled](_src_follow_promise_.followpromise.md#protected-useheadenabled)

### Methods

* [catch](_src_follow_promise_.followpromise.md#abstract-catch)
* [preFetch](_src_follow_promise_.followpromise.md#prefetch)
* [preferPush](_src_follow_promise_.followpromise.md#preferpush)
* [preferTransclude](_src_follow_promise_.followpromise.md#prefertransclude)
* [then](_src_follow_promise_.followpromise.md#abstract-then)
* [useHead](_src_follow_promise_.followpromise.md#usehead)

## Constructors

###  constructor

\+ **new FollowPromise**(): *[FollowPromise](_src_follow_promise_.followpromise.md)*

*Defined in [src/follow-promise.ts:14](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L14)*

**Returns:** *[FollowPromise](_src_follow_promise_.followpromise.md)*

## Properties

### `Protected` preferPushEnabled

• **preferPushEnabled**: *boolean*

*Defined in [src/follow-promise.ts:12](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L12)*

___

### `Protected` preferTranscludeEnabled

• **preferTranscludeEnabled**: *boolean*

*Defined in [src/follow-promise.ts:13](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L13)*

___

### `Protected` prefetchEnabled

• **prefetchEnabled**: *boolean*

*Defined in [src/follow-promise.ts:11](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L11)*

___

### `Protected` useHeadEnabled

• **useHeadEnabled**: *boolean*

*Defined in [src/follow-promise.ts:14](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L14)*

## Methods

### `Abstract` catch

▸ **catch**‹**TResult1**, **TResult2**›(`onrejected?`: function | undefined | null): *PromiseLike‹TResult1 | TResult2›*

*Defined in [src/follow-promise.ts:52](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L52)*

**Type parameters:**

▪ **TResult1**

▪ **TResult2**

**Parameters:**

Name | Type |
------ | ------ |
`onrejected?` | function &#124; undefined &#124; null |

**Returns:** *PromiseLike‹TResult1 | TResult2›*

___

###  preFetch

▸ **preFetch**(): *this*

*Defined in [src/follow-promise.ts:23](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L23)*

**Returns:** *this*

___

###  preferPush

▸ **preferPush**(): *this*

*Defined in [src/follow-promise.ts:28](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L28)*

**Returns:** *this*

___

###  preferTransclude

▸ **preferTransclude**(): *this*

*Defined in [src/follow-promise.ts:33](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L33)*

**Returns:** *this*

___

### `Abstract` then

▸ **then**‹**TResult1**, **TResult2**›(`onfulfilled?`: function | undefined | null, `onrejected?`: function | undefined | null): *PromiseLike‹TResult1 | TResult2›*

*Defined in [src/follow-promise.ts:51](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L51)*

**Type parameters:**

▪ **TResult1**

▪ **TResult2**

**Parameters:**

Name | Type |
------ | ------ |
`onfulfilled?` | function &#124; undefined &#124; null |
`onrejected?` | function &#124; undefined &#124; null |

**Returns:** *PromiseLike‹TResult1 | TResult2›*

___

###  useHead

▸ **useHead**(): *this*

*Defined in [src/follow-promise.ts:44](https://github.com/evert/ketting/blob/f7a0a1b/src/follow-promise.ts#L44)*

Use a HTTP HEAD request to fetch the links.

This is useful when interacting with servers that embed links in Link
Headers.

**Returns:** *this*
