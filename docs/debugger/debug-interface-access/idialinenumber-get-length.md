---
description: "Retrieves the number of bytes in a block."
title: "IDiaLineNumber::get_length"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaLineNumber::get_length method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaLineNumber::get_length

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the number of bytes in a block.

## Syntax

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the number of bytes in a block.

## Return Value
 If successful, returns `S_OK`. Returns `S_FALSE` if this property is not supported. Otherwise, returns an error code.

## Remarks
 The block is the length of source code on the line as represented by the [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) object.

## See also
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
