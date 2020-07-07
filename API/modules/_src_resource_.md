[ketting](../README.md) › [Globals](../globals.md) › ["src/resource"](_src_resource_.md)

# Module: "src/resource"

## Index

### Classes

* [Resource](../classes/_src_resource_.resource.md)

### Type aliases

* [StrictRequestInit](_src_resource_.md#strictrequestinit)

### Functions

* [optionsToRequestInit](_src_resource_.md#optionstorequestinit)

## Type aliases

###  StrictRequestInit

Ƭ **StrictRequestInit**: *RequestInit & object*

*Defined in [src/resource.ts:360](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L360)*

## Functions

###  optionsToRequestInit

▸ **optionsToRequestInit**(`method`: "GET", `options?`: [GetRequestOptions](_src_types_.md#getrequestoptions)): *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

*Defined in [src/resource.ts:369](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L369)*

Convert request options to RequestInit

RequestInit is passed to the constructor of fetch(). We have our own 'options' format

**Parameters:**

Name | Type |
------ | ------ |
`method` | "GET" |
`options?` | [GetRequestOptions](_src_types_.md#getrequestoptions) |

**Returns:** *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

▸ **optionsToRequestInit**(`method`: "HEAD", `options?`: [HeadRequestOptions](_src_types_.md#headrequestoptions)): *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

*Defined in [src/resource.ts:370](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L370)*

**Parameters:**

Name | Type |
------ | ------ |
`method` | "HEAD" |
`options?` | [HeadRequestOptions](_src_types_.md#headrequestoptions) |

**Returns:** *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

▸ **optionsToRequestInit**(`method`: "PATCH", `options?`: [PatchRequestOptions](_src_types_.md#patchrequestoptions)): *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

*Defined in [src/resource.ts:371](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L371)*

**Parameters:**

Name | Type |
------ | ------ |
`method` | "PATCH" |
`options?` | [PatchRequestOptions](_src_types_.md#patchrequestoptions) |

**Returns:** *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

▸ **optionsToRequestInit**(`method`: "POST", `options?`: [PostRequestOptions](_src_types_.md#postrequestoptions)): *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

*Defined in [src/resource.ts:372](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L372)*

**Parameters:**

Name | Type |
------ | ------ |
`method` | "POST" |
`options?` | [PostRequestOptions](_src_types_.md#postrequestoptions) |

**Returns:** *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

▸ **optionsToRequestInit**(`method`: "PUT", `options?`: [PutRequestOptions](_src_types_.md#putrequestoptions)): *[StrictRequestInit](_src_resource_.md#strictrequestinit)*

*Defined in [src/resource.ts:373](https://github.com/evert/ketting/blob/f7a0a1b/src/resource.ts#L373)*

**Parameters:**

Name | Type |
------ | ------ |
`method` | "PUT" |
`options?` | [PutRequestOptions](_src_types_.md#putrequestoptions) |

**Returns:** *[StrictRequestInit](_src_resource_.md#strictrequestinit)*
