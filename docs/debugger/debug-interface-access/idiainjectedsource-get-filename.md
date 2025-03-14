---
description: "Retrieves the file name for the source."
title: "IDiaInjectedSource::get_filename"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaInjectedSource::get_filename method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaInjectedSource::get_filename

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves the file name for the source.

## Syntax

```C++
HRESULT get_filename ( 
   BSTR* pRetVal
);
```

#### Parameters
 pRetVal

[out] Returns the file name for the source.

## Return Value
 If successful, returns `S_OK`. Returns `S_FALSE` if this property is not supported. Otherwise, returns an error code.

## See also
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
