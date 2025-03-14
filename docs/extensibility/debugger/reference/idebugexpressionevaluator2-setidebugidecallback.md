---
description: "Enables a debug engine to pass a callback to the expression evaluator during initialization."
title: IDebugExpressionEvaluator2::SetIDebugIDECallback
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
author: maiak
ms.author: maiak
manager: jmartens
ms.technology: vs-ide-debug
dev_langs:
- CPP
- CSharp
---
# IDebugExpressionEvaluator2::SetIDebugIDECallback

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Enables a debug engine to pass a callback to the expression evaluator during initialization.

## Syntax

### [C#](#tab/csharp)
```csharp
int SetIDebugIDECallback (
   IDebugIDECallback pCallback
);
```
### [C++](#tab/cpp)
```cpp
HRESULT SetIDebugIDECallback (
   IDebugIDECallback * pCallback
);
```
---

## Parameters
`pCallback`\
[in] Interface for the callback.

## Return Value
 If successful, returns `S_OK`; otherwise, returns an error code.

## See also
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
