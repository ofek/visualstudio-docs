---
description: "Gets the system thread identifier."
title: IDebugThread2::GetThreadId
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
author: maiak
ms.author: maiak
manager: jmartens
ms.technology: vs-ide-debug
dev_langs:
- CPP
- CSharp
---
# IDebugThread2::GetThreadId

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Gets the system thread identifier.

## Syntax

### [C#](#tab/csharp)
```csharp
int GetThreadId (
    out uint pdwThreadId
);
```
### [C++](#tab/cpp)
```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```
---

## Parameters
`pdwThreadId`\
[out] Returns the system thread identifier.

## Return Value
If successful, returns `S_OK`; otherwise, returns an error code.

## Remarks
A thread ID is used to identify a thread among all other threads in a process.

## Example
The following example shows how to implement this method for a simple `CProgram` object that implements the [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interface.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## See also
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
