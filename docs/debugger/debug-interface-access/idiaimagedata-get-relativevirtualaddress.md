---
description: "Retrieves the location in virtual memory of the module relative to the application."
title: "IDiaImageData::get_relativeVirtualAddress"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaImageData::get_relativeVirtualAddress method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaImageData::get_relativeVirtualAddress

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the location in virtual memory of the module relative to the application.

## Syntax

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns the relative virtual memory offset of the module.

## Return Value
 If successful, returns `S_OK`; otherwise, returns an error code.

## See also
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
