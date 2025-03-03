---
description: "Retrieves the name of the file from which the symbols were loaded."
title: "IDiaSymbol::get_symbolsFileName"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaSymbol::get_symbolsFileName method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaSymbol::get_symbolsFileName

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the name of the file from which the symbols were loaded.

## Syntax

```C++
HRESULT get_symbolsFileName ( 
   BSTR* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the name of the file from which the symbols were loaded.

## Return Value
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` or an error code.

> [!NOTE]
> A return value of `S_FALSE` means the property is not available for the symbol.

## Remarks
 This property is valid only for symbols with a [SymTagEnum Enumeration](../../debugger/debug-interface-access/symtagenum.md) value of `SymTagExe` that also have global scope.

## See also
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Enumeration](../../debugger/debug-interface-access/symtagenum.md)
