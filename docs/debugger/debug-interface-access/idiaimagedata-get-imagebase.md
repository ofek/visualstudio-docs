---
description: "Retrieves the memory location where the image should be based."
title: "IDiaImageData::get_imageBase"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaImageData::get_imageBase method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaImageData::get_imageBase

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the memory location where the image should be based.

## Syntax

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the suggested image base value.

## Return Value
 If successful, returns `S_OK`; otherwise, returns an error code.

## Remarks
 Due to image base conflicts, an image may be rebased automatically to an unused memory location when it is loaded. This method returns the base hint (suggested memory location) that was stored in the module at compile time.

## See also
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
