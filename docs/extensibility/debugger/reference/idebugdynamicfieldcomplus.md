---
description: "Represents a dynamic field for an IDebugBinder object."
title: IDebugDynamicFieldCOMPlus
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
author: maiak
ms.author: maiak
manager: jmartens
ms.technology: vs-ide-debug
---
# IDebugDynamicFieldCOMPlus

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Represents a dynamic field for an [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) object.

## Syntax

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## Methods
 In addition to the methods on the [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) interface, this interface implements the following methods:

|Method|Description|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Retrieves a type given its primitive type.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Retrieves a type given its token.|

## Requirements
 Header: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
