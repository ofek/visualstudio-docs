---
title: Programmatically search for text in worksheet ranges (Visual Studio)
description: Search for text within a specific Microsoft Office Excel worksheet range programmatically from Visual Basic or C# in Visual Studio.
titleSuffix: ""
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "worksheets, searching"
  - "text [Office development in Visual Studio], searching in worksheets"
  - "text searches, worksheets"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically search for Text in worksheet ranges

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  The <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> method of the <xref:Microsoft.Office.Interop.Excel.Range> object enables you to search for text within the range. This text can also be any of the error strings that can appear in a worksheet cell such as `#NULL!` or `#VALUE!`. For more information about error strings, see [Cell error values](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 The following example searches a range named `Fruits` and modifies the font for cells that contain the word "apples". This procedure also uses the <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> method, which uses the previously set search settings to repeat the search. You specify the cell after which to search, and the <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> method handles the rest.

> [!NOTE]
> The <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> method's search wraps back to the beginning of the search range after it has reached the end of the range. Your code must ensure that the search does not wrap around in an infinite loop. The sample procedure shows one way to handle this using the <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> property.

## To search for text in a worksheet range

1. Declare variables for tracking the entire range, the first found range, and the current found range.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::
    ---

2. Search for the first match, specifying all the parameters except the cell to search after.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::
    ---

3. Continue searching as long as there are matches.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::
    ---

4. Compare the first found range (`firstFind`) to **Nothing**. If `firstFind` contains no value, the code stores away the found range (`currentFind`).

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::
    ---

5. Exit the loop if the address of the found range matches the address of the first found range.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::
    ---

6. Set the appearance of the found range.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::
    ---

7. Perform another search.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::
    ---

   The following example shows the complete method.

## Example

 ### [C#](#tab/csharp)
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::

 ### [VB](#tab/vb)
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57"::: ---

## Related content
- [Work with ranges](../vsto/working-with-ranges.md)
- [How to: Programmatically apply styles to ranges in workbooks](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [How to: Programmatically refer to worksheet ranges in code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Optional parameters in Office solutions](../vsto/optional-parameters-in-office-solutions.md)
