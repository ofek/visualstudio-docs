---
title: "Collapse ranges or selections in documents programmatically"
description:  Learn that if you are working with a Range or Selection object, you might want to change the selection to an insertion point before inserting text.
titleSuffix: ""
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "selections, collapsing"
  - "documents [Office development in Visual Studio], collapsing ranges"
  - "collapsing selections"
  - "ranges, collapsing"
  - "collapsing ranges"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically collapse ranges or selections in documents

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  If you are working with a <xref:Microsoft.Office.Interop.Word.Range> or <xref:Microsoft.Office.Interop.Word.Selection> object, you might want to change the selection to an insertion point before inserting text, to avoid overwriting existing text. Both the <xref:Microsoft.Office.Interop.Word.Range> and <xref:Microsoft.Office.Interop.Word.Selection> objects have a Collapse method, which makes use of the <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> enumeration values:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> collapses the selection to the beginning of the selection. This is the default if you do not specify an enumeration value.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> collapses the selection to the end of the selection.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## To collapse a range and insert new text

1. Create a <xref:Microsoft.Office.Interop.Word.Range> object that consists of the first paragraph in the document.

    The following code example can be used in a document-level customization.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    ---

    The following code example can be used in a VSTO Add-in. This code uses the active document.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    ---

2. Use the <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> enumeration value to collapse the range.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    ---

3. Insert the new text.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    ---

4. Select the <xref:Microsoft.Office.Interop.Word.Range>.

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    ---

   If you use the <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> enumeration value, the text is inserted at the beginning of the following paragraph.

   ### [C#](#tab/csharp)
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   ### [VB](#tab/vb)
   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   ---

   You might expect that inserting a new sentence would insert it before the paragraph marker, but that is not the case because the original range includes the paragraph marker. 

## Document-level customization example

### To collapse a range in a document-level customization

1. The following example shows the complete method for a document-level customization. To use this code, run it from the `ThisDocument` class in your project.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     ---

## VSTO Add-in example

### To collapse a range in a VSTO Add-in

1. The following example shows the complete method for a VSTO Add-in. To use this code, run it from the `ThisAddIn` class in your project.

     ### [C#](#tab/csharp)
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

     ### [VB](#tab/vb)
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     ---

## Related content
- [How to: Programmatically insert text into Word documents](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [How to: Programmatically define and select ranges in documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programmatically retrieve start and end characters in ranges](/previous-versions/visualstudio/visual-studio-2017/vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges)
- [How to: Programmatically extend ranges in documents](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programmatically reset ranges in Word documents](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
