[ketting](../README.md) › [Globals](../globals.md) › ["src/types"](_src_types_.md)

# Module: "src/types"

## Index

### Type aliases

* [GetRequestOptions](_src_types_.md#getrequestoptions)
* [HeadRequestOptions](_src_types_.md#headrequestoptions)
* [HttpHeaders](_src_types_.md#httpheaders)
* [PatchRequestOptions](_src_types_.md#patchrequestoptions)
* [PostRequestOptions](_src_types_.md#postrequestoptions)
* [PutRequestOptions](_src_types_.md#putrequestoptions)
* [RequestOptions](_src_types_.md#requestoptions)

## Type aliases

###  GetRequestOptions

Ƭ **GetRequestOptions**: *Omit‹[RequestOptions](_src_types_.md#requestoptions), "serializeBody" | "data"›*

*Defined in [src/types.ts:41](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L41)*

___

###  HeadRequestOptions

Ƭ **HeadRequestOptions**: *[GetRequestOptions](_src_types_.md#getrequestoptions)*

*Defined in [src/types.ts:42](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L42)*

___

###  HttpHeaders

Ƭ **HttpHeaders**: *Record‹string, string›*

*Defined in [src/types.ts:1](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L1)*

___

###  PatchRequestOptions

Ƭ **PatchRequestOptions**: *[RequestOptions](_src_types_.md#requestoptions)‹T›*

*Defined in [src/types.ts:43](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L43)*

___

###  PostRequestOptions

Ƭ **PostRequestOptions**: *[RequestOptions](_src_types_.md#requestoptions)‹T›*

*Defined in [src/types.ts:45](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L45)*

___

###  PutRequestOptions

Ƭ **PutRequestOptions**: *[RequestOptions](_src_types_.md#requestoptions)‹T›*

*Defined in [src/types.ts:44](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L44)*

___

###  RequestOptions

Ƭ **RequestOptions**: *object*

*Defined in [src/types.ts:9](https://github.com/evert/ketting/blob/f7a0a1b/src/types.ts#L9)*

RequestOptions is a set of properties that define
a request, or state change.

Everything is usually optional.

#### Type declaration:

* **data**? : *T*

* **getContentHeaders**? : *undefined | function*

* **headers**? : *[HttpHeaders](_src_types_.md#httpheaders) | Headers*

* **serializeBody**? : *undefined | function*
