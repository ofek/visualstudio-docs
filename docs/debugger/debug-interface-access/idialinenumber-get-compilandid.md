---
description: "Retrieves a unique identifier for the compiland that contributed this line."
title: "IDiaLineNumber::get_compilandId"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaLineNumber::get_compilandId method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaLineNumber::get_compilandId

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves a unique identifier for the compiland that contributed this line.

## Syntax

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns `DWORD` that contains the unique identifier for the compiland that contributed this line.

## Return Value
 If successful, returns `S_OK`. Returns `S_FALSE` if this property is not supported. Otherwise, returns an error code.

## See also
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
