---
title: CvIsEnabled Function
description: See reference information for the Concurrency Visualizer SDK function CvIsEnabled (C library).
ms.date: 11/04/2016
ms.topic: reference
f1_keywords: 
  - cvmarkers/CvIsEnabledEx
  - cvmarkers/CvIsEnabled
helpviewer_keywords: 
  - CvIsEnabled method
  - CvIsEnabledEx method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
---
# CvIsEnabled function

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Determines whether any session has enabled the specified ETW provider.

## Syntax

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### Parameters
 `category`
 Category.

 `level`
 Importance level.

 `pProvider`
 Valid provider object. Cannot be NULL.

## Return value
 S_OK if provider is currently enabled. S_FALSE if provider is currently disabled. Error code in case there were any errors. Use FAILED macro to check for error condition and then check for S_OK/S_FALSE.

## Requirements
 **Header:** *cvmarkers.h*

## See also
- [C++ library reference](../profiling/cpp-library-reference.md)