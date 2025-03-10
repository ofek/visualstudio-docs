---
title: "Map ListObject columns to data"
description: Learn how you can map which columns you want to appear in the ListObject when you call the SetDataBinding method.
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "data [Office development in Visual Studio], mapping to ListObject column"
  - "ListObject control, mapping data"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Map ListObject columns to data

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  When you bind a <xref:Microsoft.Office.Tools.Excel.ListObject> control to a <xref:System.Data.DataTable>, you might not want to display all the columns in a list, or you might have certain columns that are not bound to data. You can map which columns you want to appear in the <xref:Microsoft.Office.Tools.Excel.ListObject> when you call the <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> method.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## Map columns

### To map a data table to columns in a list

1. Create the <xref:System.Data.DataTable> at the class level.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::
     ---

2. Add sample columns and data in the `Startup` event handler of the `Sheet1` class (in a document-level project) or `ThisAddIn` class (in a VSTO Add-in project).

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::
     ---

3. Call the <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> method and pass in the column names in the order they should appear. The list object will be bound to the newly created <xref:System.Data.DataTable>, but the order of the columns in the list object will differ from the order they appear in the <xref:System.Data.DataTable>.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::
     ---

## Specify unmapped columns
 When you map columns to a <xref:System.Data.DataTable>, you can also specify that certain columns should not be bound to data by passing in an empty string. A new column that is not bound to data is then added to the <xref:Microsoft.Office.Tools.Excel.ListObject> control.

### To specify an unmapped column when mapping ListObject columns

1. Call the <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> method and pass in the column names in the order they should appear. Use an empty string to indicate where an unmapped column is added; in this case, between the title column and the last name column.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::
     ---

## Compile the code
 This code example assumes you have an existing <xref:Microsoft.Office.Tools.Excel.ListObject> named `list1` on the worksheet in which this code appears.

## Related content
- [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controls on Office documents](../vsto/controls-on-office-documents.md)
- [Add controls to Office documents at run time](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [How to: Fill ListObject controls with data](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automate Excel by using extended objects](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject control](../vsto/listobject-control.md)
