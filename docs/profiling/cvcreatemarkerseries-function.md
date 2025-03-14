---
title: CvCreateMarkerSeries Function
description: See reference information for the Concurrency Visualizer SDK function CvCreateMarkerSeries (C library).
ms.date: 11/04/2016
ms.topic: reference
f1_keywords: 
  - cvmarkers/CvCreateMarkerSeriesA
  - cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords: 
  - CvCreateMarkerSeriesA method
  - CvCreateMarkerSeriesW method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
---
# CvCreateMarkerSeries function

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Creates marker series for a given provider.

## Syntax

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### Parameters
 `pProvider`
 Provider object previously initialized by CvInitProvider. Cannot be NULL.

 `pSeriesName`
 Marker series name. Cannot be NULL but empty string is allowed.

 `ppMarkerSeries`
 Address of an output variable which will store marker series context. Cannot be NULL.

## Return value
 S_OK when marker series is successfully created or error code in case there were any errors. Use SUCCEEDED/FAILED macros to check for error condition.

## Requirements
 **Header:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## See also
- [C++ library reference](../profiling/cpp-library-reference.md)