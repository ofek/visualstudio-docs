---
description: "Gets the port supplier for this port."
title: IDebugPort2::GetPortSupplier
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
author: maiak
ms.author: maiak
manager: jmartens
ms.technology: vs-ide-debug
dev_langs:
- CPP
- CSharp
---
# IDebugPort2::GetPortSupplier

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Gets the port supplier for this port.

## Syntax

### [C#](#tab/csharp)
```csharp
int GetPortSupplier( 
   out IDebugPortSupplier2 ppSupplier
);
```
### [C++](#tab/cpp)
```cpp
HRESULT GetPortSupplier( 
   IDebugPortSupplier2** ppSupplier
);
```
---

## Parameters
`ppSupplier`\
[out] Returns an [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) object represents the port supplier for a port.

## Return Value
 If successful, returns `S_OK`; otherwise, returns an error code.

## See also
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
