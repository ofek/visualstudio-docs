---
title: "Programmatically list all worksheets in a workbook"
description: Learn how you can programmatically list all worksheets in a Microsoft Excel workbook by using Visual Studio.
titleSuffix: ""
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "workbooks, listing worksheets"
  - "worksheets, listing"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically list all worksheets in a workbook

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  The <xref:Microsoft.Office.Interop.Excel.Workbook> class provides a <xref:Microsoft.Office.Interop.Excel.Worksheets> object. This object contains a collection of all the <xref:Microsoft.Office.Interop.Excel.Worksheet> objects in the workbook.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## To list all existing worksheets in a workbook in a document-level customization

1. Iterate through the <xref:Microsoft.Office.Interop.Excel.Worksheets> collection and send the name of each sheet to a cell offset from a <xref:Microsoft.Office.Tools.Excel.NamedRange> control.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet21":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet21":::
     ---

## To list all existing worksheets in a workbook in a VSTO Add-in

1. Iterate through the <xref:Microsoft.Office.Interop.Excel.Worksheets> collection and send the name of each sheet to a cell offset from a <xref:Microsoft.Office.Interop.Excel.Range> object.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet13":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet13":::
     ---

## Related content
- [Work with worksheets](../vsto/working-with-worksheets.md)
- [How to: Programmatically add new worksheets to workbooks](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [How to: Programmatically move worksheets within workbooks](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Global access to objects in Office projects](../vsto/global-access-to-objects-in-office-projects.md)
