---
title: "Programmatically use built-in dialog boxes in Word"
description: Learn how you can use Visual Studio to programmatically use built-in dialog boxes in Microsoft Word.
titleSuffix: ""
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "Word [Office development in Visual Studio], dialog boxes"
  - "dialog boxes, Word"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically use built-in dialog boxes in Word

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  When working with Microsoft Office Word, there are times when you need to display dialog boxes for user input. Although you can create your own, you might also want to take the approach of using the built-in dialog boxes in Word, which are exposed in the <xref:Microsoft.Office.Interop.Word.Dialogs> collection of the <xref:Microsoft.Office.Interop.Word.Application> object. This enables you to access over 200 of the built-in dialog boxes, which are represented as enumerations.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## Display dialog boxes
 To display a dialog box, use one of the values of the <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumeration to create a <xref:Microsoft.Office.Interop.Word.Dialog> object that represents the dialog box you want to display. Then, call the <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> method of the <xref:Microsoft.Office.Interop.Word.Dialog> object.

 The following code example demonstrates how to display the **File Open** dialog box. To use this example, run it from the `ThisDocument` or `ThisAddIn` class in your project.

 ### [C#](#tab/csharp)
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

 ### [VB](#tab/vb)
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 ---

### Access dialog box members that are available through late binding
 Some properties and methods of dialog boxes in Word are available only through late binding. In Visual Basic projects where **Option Strict** is on, you must use reflection to access these members. For more information, see [Late binding in Office solutions](../vsto/late-binding-in-office-solutions.md).

 The following code example demonstrates how to use the **Name** property of the **File Open** dialog box in Visual Basic projects where **Option Strict** is off or in Visual C# projects that target the .NET Framework 4 or the .NET Framework 4.5. To use this example, run it from the `ThisDocument` or `ThisAddIn` class in your project.

 ### [C#](#tab/csharp)
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 ### [VB](#tab/vb)
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 ---

 The following code example demonstrates how to use reflection to access the **Name** property of the **File Open** dialog box in Visual Basic projects where **Option Strict** is on. To use this example, run it from the `ThisDocument` or `ThisAddIn` class in your project.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## Related content
- [How to: Programmatically use Word dialog boxes in hidden mode](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word object model overview](../vsto/word-object-model-overview.md)
- [Optional parameters in Office solutions](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
