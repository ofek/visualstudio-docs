---
title: "Programmatically remove protection from worksheets"
description: Learn how you can use Visual Studio to programmatically remove protection from a Microsoft Excel worksheet.
titleSuffix: ""
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "worksheets, unprotecting"
  - "documents [Office development in Visual Studio], document protection"
  - "document protection, removing from worksheets"
  - "Unprotect method"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically remove protection from worksheets

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  You can programmatically remove protection from a Microsoft Office Excel worksheet.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 The following example uses the variable `getPasswordFromUser`, which contains a password obtained from the user.

## To unprotect a worksheet in a document-level customization

1. Call the <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> method of the worksheet and pass in the password, if necessary. This example assumes that you are working with a worksheet named `Sheet1`.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::
     ---

## To unprotect a worksheet in a VSTO Add-in

1. Call the <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> method of the active worksheet and pass in the password, if necessary.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::
     ---

## Related content
- [Work with worksheets](../vsto/working-with-worksheets.md)
- [How to: Programmatically protect worksheets](../vsto/how-to-programmatically-protect-worksheets.md)
- [How to: Programmatically protect workbooks](../vsto/how-to-programmatically-protect-workbooks.md)
- [How to: Programmatically hide worksheets](../vsto/how-to-programmatically-hide-worksheets.md)
- [Global access to objects in Office projects](../vsto/global-access-to-objects-in-office-projects.md)
