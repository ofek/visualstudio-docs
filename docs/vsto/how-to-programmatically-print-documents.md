---
title: "Programmatically print documents"
description: Learn how you can print an entire Microsoft Word document, or part of a document, to your default printer.
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "Word [Office development in Visual Studio], printing documents"
  - "documents [Office development in Visual Studio], printing"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically print documents

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  You can print an entire Microsoft Office Word document, or part of a document, to your default printer.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## Print a document that is part of a document-level customization

### To print the entire document

1. Call the <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> method of the `ThisDocument` class in your project to print the entire document. To use this example, run the code from the `ThisDocument` class.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet11":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet11":::
     ---

### To print the current page of the document

1. Call the <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> method of the `ThisDocument` class in your project and specify that one copy of the current page be printed. To use this example, run the code from the `ThisDocument` class.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet12":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet12":::
     ---

## Print a document by using a VSTO Add-in

### To print an entire document

1. Call the <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> method of the <xref:Microsoft.Office.Interop.Word.Document> object that you want to print. The following code example prints the active document. To use this example, run the code from the `ThisAddIn` class in your project.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet11":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet11":::
     ---

### To print the current page of a document

1. Call the <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> method of the <xref:Microsoft.Office.Interop.Word.Document> object that you want to print, and specify that one copy of the current page be printed. The following code example prints the active document. To use this example, run the code from the `ThisAddIn` class in your project.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet12":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet12":::
     ---

## Related content
- [Optional parameters in Office solutions](../vsto/optional-parameters-in-office-solutions.md)
