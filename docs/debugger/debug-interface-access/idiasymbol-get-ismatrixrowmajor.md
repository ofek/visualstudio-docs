---
description: "Specifies whether the matrix is row major."
title: "IDiaSymbol::get_isMatrixRowMajor"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaSymbol::get_isMatrixRowMajor

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Specifies whether the matrix is row major.

## Syntax

```C++
HRESULT get_isMatrixRowMajor(
   BOOL* pRetVal);
```

#### Parameters
 `pRetVal`

[out] A pointer to a `BOOL` that specifies whether the matrix is row major.

## Return Value
 If successful, returns `S_OK`; otherwise, returns `S_FALSE` or an error code.

## See also
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
