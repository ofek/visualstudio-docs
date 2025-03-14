---
title: "Programmatically open workbooks"
description: Open or work with an existing Microsoft Office Excel workbook programmatically from Visual Basic or C# in Visual Studio.
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "workbooks, opening"
  - "Excel [Office development in Visual Studio], opening workbooks"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically open workbooks

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  The <xref:Microsoft.Office.Interop.Excel.Workbooks> collection in Microsoft Office Excel makes it possible to work with all open workbooks and to open workbooks.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## To open an existing workbook

1. Use the <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> method of the <xref:Microsoft.Office.Interop.Excel.Workbooks> collection, passing in the path to the workbook.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::
     ---

## Compile the code
 This code example requires the following:

- A workbook named `YourWorkbook.xls` must exist in a directory named `Test` on drive C.

## Related content
- [Work with workbooks](../vsto/working-with-workbooks.md)
- [How to: Programmatically open text files as workbooks](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [How to: Programmatically create new workbooks](../vsto/how-to-programmatically-create-new-workbooks.md)
- [How to: Programmatically save workbooks](../vsto/how-to-programmatically-save-workbooks.md)
- [How to: Programmatically close workbooks](../vsto/how-to-programmatically-close-workbooks.md)
- [Programmatic limitations of host items and host controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optional parameters in Office solutions](../vsto/optional-parameters-in-office-solutions.md)
- [Host items and host controls overview](../vsto/host-items-and-host-controls-overview.md)
