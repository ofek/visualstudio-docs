---
description: "Retrieves the undecorated name for a C++ decorated, or linkage, name."
title: "IDiaSymbol::get_undecoratedName"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaSymbol::get_undecoratedName method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaSymbol::get_undecoratedName

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the undecorated name for a C++ decorated, or linkage, name.

## Syntax

```C++
HRESULT get_undecoratedName ( 
   BSTR* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the undecorated name for a C++ decorated name.

## Return Value
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` or an error code.

> [!NOTE]
> A return value of `S_FALSE` means the property is not available for the symbol.

## See also
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
