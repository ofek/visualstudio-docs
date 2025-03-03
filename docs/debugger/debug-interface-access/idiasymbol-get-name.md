---
description: "Retrieves the name of the symbol."
title: "IDiaSymbol::get_name"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaSymbol::get_name method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaSymbol::get_name

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the name of the symbol.

## Syntax

```C++
HRESULT get_name ( 
   BSTR* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the name of the symbol.

## Return Value
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` or an error code.

> [!NOTE]
> A return value of `S_FALSE` means the property is not available for the symbol.

## Example

```C++
IDiaSymbol* pType;
BSTR        name;
pType->get_name( &name );
```

## See also
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
