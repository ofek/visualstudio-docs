---
description: "Retrieves a flag that indicates whether the section is a COMDAT record."
title: "IDiaSectionContrib::get_comdat"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaSectionContrib::get_comdat method"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# IDiaSectionContrib::get_comdat

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Retrieves a flag that indicates whether the section is a COMDAT record.

## Syntax

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### Parameters
 `pRetVal`

[out] Returns `TRUE` if the section is a COMDAT record; otherwise, returns `FALSE`.

## Return Value
 If successful, returns `S_OK`. Returns `S_FALSE` if this property is not supported. Otherwise, returns an error code.

## Remarks
 A COMDAT record is a Common Object File Format (COFF) record that makes packaged functions visible to the linker.

## See also
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
