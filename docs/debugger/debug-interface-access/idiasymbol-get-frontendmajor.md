---
description: "Retrieves the front end major version number."
title: "IDiaSymbol::get_frontEndMajor"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaSymbol::get_frontEndMajor method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaSymbol::get_frontEndMajor

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the front end major version number.

## Syntax

```C++
HRESULT get_frontEndMajor ( 
   DWORD* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the front end major version number. See Remarks.

## Return Value
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` or an error code.

> [!NOTE]
> A return value of `S_FALSE` means that the property is not available for the symbol.

## Remarks
 A compiler is typically composed of two primary elements: the front end (the parser), which handles parsing the source code into an intermediate form, and a back end (code generator), which converts the intermediate form into assembly. It is not uncommon for the front end to have a different version than the back end.

 A front end or back end version number is composed of three parts: \<major>.\<minor>.\<build>, where \<major> is the major version number, \<minor> is the minor version number, and \<build> is the build number. For example, 13.10.3077.

## Requirements

|Requirement|Description|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA SDK v7.0|

## See also
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
