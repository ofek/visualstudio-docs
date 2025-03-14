---
title: Collapse and expand regions of code
description: Use the expand and collapse commands in the Visual Studio integrated development environment (IDE) to work in outline mode.
ms.date: 05/22/2023
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
---
# Outlining

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

To hide a region of code from view, you can collapse it so that it appears under a plus sign (**+**) in the text editor. Then, to expand a collapsed region, select the plus sign.

> [!TIP]
> If you are a keyboard user, you can choose **Ctrl**+**M**+**M** to collapse and expand.

To collapse an outlining region, double-click any line in the region on the outlining margin, which appears just to the left of the code. You can see the contents of a collapsed region as a tooltip when you hover over the collapsed region.

:::image type="content" source="media/outlining-example.png" alt-text="Screenshot of an example of collapsed code that shows the outlining margin and an example of the expanded code visible from a tooltip." lightbox="media/outlining-example.png":::

Regions in the outlining margin are also highlighted when you hover over the margin with the mouse. The default highlighting color may seem rather faint in some color configurations. You can change it in **Tools** > **Options** > **Environment** > **Fonts and Colors** > **Collapsible Region**.

When you work in outlined code, you can expand the sections you want to work on, collapse them when you're done, and then move to other sections. When you don't want to have outlining displayed, you can use the **Stop Outlining** command to remove the outline information without disturbing your underlying code.

The **Undo** and **Redo** commands on the **Edit** menu affect these actions. The **Copy**, **Cut**, **Paste**, and drag-and-drop operations retain outlining information, but not the state of the collapsible region. For example, when you copy a region that's collapsed, the **Paste** operation pastes the copied text as an expanded region.

> [!CAUTION]
> When you change an outlined region, the outlining may be lost. For example, deletions or **Find and Replace** operations may erase the end of the region.

The following commands can be found on the **Edit** > **Outlining** submenu.

|Name|Description|
|-|-|
|Hide Selection|(**Ctrl**+**M**, **Ctrl**+**H**) - Collapses a selected block of code that wouldn't normally be available for outlining, for example an `if` block. To remove the custom region, use **Stop Hiding Current** (or **Ctrl**+**M**, **Ctrl**+**U**). Not available in Visual Basic.|
|Toggle Outlining Expansion| (**Ctrl**+**M**, **Ctrl**+**M**) - Reverses the current hidden or expanded state of the innermost outlining section when the cursor lies in a nested collapsed section.|
|Toggle All Outlining|(**Ctrl**+**M**, **Ctrl**+**L**) - Sets all regions to the same collapsed or expanded state. If some regions are expanded and some collapsed, then the collapsed regions are expanded.|
|Stop Outlining|(**Ctrl**+**M**, **Ctrl**+**P**) - Removes all outlining information for the entire document. <br>(To turn it back on, go to **Edit** > **Outlining** and select **Start Automatic Outlining**.)|
|Stop Hiding Current|(**Ctrl**+**M**, **Ctrl**+**U**)  - Removes the outlining information for the currently selected user-defined region. Not available in Visual Basic.|
|Collapse to Definitions|(**Ctrl**+**M**, **Ctrl**+**O**) - Collapses the members of all types.|
|Collapse Block:\<logical boundary>|(C++) Collapses a region in the function containing the insertion point. For example, if the insertion point lies inside a loop, the loop is hidden.|
|Collapse All in: \<logical structures>|(C++) Collapses all the structures inside the function.|

> [!TIP]
> For more information on how to use the keyboard exclusively, see [Keyboard shortcuts in Visual Studio](default-keyboard-shortcuts-in-visual-studio.md).

You can also use the Visual Studio SDK to define the text regions you want to expand or collapse. See [Walkthrough: Outlining](../extensibility/walkthrough-outlining.md).

## Related content

- [Features of the code editor](writing-code-in-the-code-and-text-editor.md)
- [Source editor (Visual Studio for Mac)](/visualstudio/mac/source-editor)
