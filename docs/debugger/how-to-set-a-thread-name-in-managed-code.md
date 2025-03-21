---
title: Set a Thread Name in Managed Code
description: Set a thread name in managed code during multithreaded app debugging in Visual Studio. Thread naming is used to keep track of threads in the Threads window.
ms.date: 04/27/2017
ms.topic: how-to
dev_langs: 
  - CSharp
  - VB
  - FSharp
  - C++
helpviewer_keywords: 
  - Thread.Name property
  - threading [Visual Studio], names
  - thread names
  - debugging [Visual Studio], threads
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
---
# Set a Thread Name in Managed Code

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Thread naming is possible in any edition of Visual Studio. Thread naming is useful for keeping track of threads in the **Threads** window.

 To set a thread name in managed code, use the <xref:System.Threading.Thread.Name%2A> property.

## Example

### [C#](#tab/csharp)
```csharp
public class Needle
{
    // This method will be called when the thread is started.
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate
    oThread.Start();
}
```

### [VB](#tab/vb)
```VB
Public Class Needle
    ' This method will be called when the thread is started.
    Sub Baz()
        Console.WriteLine("Needle Baz is running on another thread")
    End Sub
End Class

Sub Main()
    Console.WriteLine("Thread Simple Sample")
    Dim oNeedle As New Needle()
   ' Create a Thread object.
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)
    ' Set the Thread name to "MyThread".
    oThread.Name = "MyThread"
    ' Starting the thread invokes the ThreadStart delegate
    oThread.Start()
End Sub
```
---

## See also
- [Debug Multithreaded Applications](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [How to: Set a Thread Name in Native Code](../debugger/how-to-set-a-thread-name-in-native-code.md)