---
title: "Programmatically determine the current Outlook item"
description: Learn how you can programmatically determine the current Microsoft Outlook item. This example uses the Explorer.SelectionChange event.
titleSuffix: ""
ms.date: "02/02/2017"
ms.topic: "how-to"
dev_langs:
  - "VB"
  - "CSharp"
helpviewer_keywords:
  - "mail items [Office development in Visual Studio], current"
  - "e-mail [Office development in Visual Studio], current item"
  - "SelectionChange event"
  - "Outlook [Office development in Visual Studio], current item"
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
---
# Programmatically determine the current Outlook item

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
  This example uses the `Explorer.SelectionChange` event to display the name of the current folder and some information about the selected item. The code then displays the selected item.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## Example

 ### [C#](#tab/csharp)
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

 ### [VB](#tab/vb)
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 ---

## Compile the code
 This example requires:

- Appointment, contact, and e-mail items in Microsoft Office Outlook.

## Related content
- [Outlook object model overview](../vsto/outlook-object-model-overview.md)
- [How to: Programmatically retrieve a folder by name](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [How to: Programmatically search for a specific contact](/previous-versions/visualstudio/visual-studio-2017/vsto/how-to-programmatically-search-for-a-specific-contact)
