---
title: Use Visual Studio search to find code & do queries
description: Explore the Visual Studio search feature and discover how to find settings, menus, code, and work with filters, queries, and more.
ms.date: 08/08/2023
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
monikerRange: ">=vs-2019"
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-ide-general
---
# Use Visual Studio search

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

The Visual Studio integrated development environment (IDE) has many menus, options, and features, which can be difficult to remember. The Visual Studio search feature is a single search box that helps developers find IDE menus and options, while also searching your code. Whether you're new to Visual Studio or an experienced developer, this feature offers a quick way to search across IDE features and your code.

::: moniker range=">=vs-2022"

## Search in Visual Studio 2022 version 17.6 or later

If you're using Visual Studio 2022 [version 17.6](/visualstudio/releases/2022/release-notes-v17.6) or later, you have access to a new search experience: **All-In-One Search**. 

### About the All-In-One Search experience

With **All-In-One Search**, not only can you search for features, but now you can search your code elements, too.

:::image type="content" source="media/vs-2022/all-one-search.png" alt-text="Screenshot of the All-In-One Search experience in Visual Studio 2022 version 17.6 or later."::: 

To enable this feature, go to **Tools** > **Options** > **Environment** > **Preview Features** > **New Visual Studio Search experience**.

:::image type="content" source="media/vs-2022/all-one-search-tools-options.png" alt-text="Screenshot of the Tools Options menu in Visual Studio 2022 that shows how to toggle the All-In-One Search experience.":::

After you enable **All-In-One Search** and restart Visual Studio, the new search experience appears as an option next to the menu bar. 

:::image type="content" source="media/vs-2022/all-one-search-from-menu-bar.png" alt-text="Screenshot of the All-In-One Search experience from the Visual Studio menu bar.":::

#### Keyboard shortcuts for search

You can use the **Ctrl**+**Q** keyboard shortcut for feature searches, and the **Ctrl**+**T** keyboard shortcut for code searches. 

#### Filters for queries

To quickly get a filtered experience, you can type the corresponding prefixes before your query or use the corresponding keyboard shortcuts to open the search with the filter you want.

|Filter   |Prefix   |Keyboard shortcut               |
|---------|---------|--------------------------------|
|files    |`f:`     | **Ctrl**+**Shift**+**T**       |     
|types    |`t:`     | **Ctrl**+**1**, **Ctrl**+**T** |
|members  |`m:`     | **Alt**+**\\**                 |

> [!TIP]
> To learn more about the new search experience, see both the [Better search in Visual Studio](https://devblogs.microsoft.com/visualstudio/new-better-search-in-visual-studio/) and [All-In-One Search available in 17.6](https://devblogs.microsoft.com/visualstudio/all-in-one-search-available-in-17-6/) blog posts.

::: moniker-end

## Search in Visual Studio 2022 version 17.5 or earlier

The following sections discuss the different types of search results you can find if you're using Visual Studio 2022 version 17.5 or earlier (to include Visual Studio 2019).

Unlike other search features such as [Find in Files](find-in-files.md) or Search Solution Explorer, the search results in Visual Studio include IDE features, menu options, file names, and more. To access it, use the **Ctrl**+**Q** keyboard shortcut to view the search box. Or, select the Visual Studio Search input box, which is located next to the menu bar:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Screenshot of the Visual Studio search box." lightbox="media/visual-studio-search.png":::

> [!NOTE]
> The command executed by Visual Studio search is `Window.QuickLaunch` and you might see this feature referred to as quick search or quick launch.

### Search menus, options, and windows

You can use the Visual Studio search box to find settings, options, and similar configuration items. For example, search for *change theme* to quickly find and open the dialog that allows you to change the Visual Studio color theme as shown in the following screenshot:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Search Visual Studio settings and options.":::

> [!TIP]
> In most cases Visual Studio search will also remind you of the menu, shortcut keys, and location of each item in the results.

You can use the Visual Studio search box to find menu items and commands. For example, search for *clean sol* to quickly find and execute the Clean Solution command. The search results also offer a reminder of where to find this command in the menus as shown in the following screenshot:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Screenshot of an example of a search for Visual Studio menu items and commands.":::

Finally, you can search for windows or panels that you might have accidentally closed. For example, search for *test* to find and open the Test Explorer window:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Screenshot that shows an example of a search for Visual Studio windows and panels.":::

### Search files and code

Visual Studio search also searches your solution items for filename, code, method, and other matches. In the following screenshot, a search for *markdown* has found the MarkdownMetaExtractor.cs file, the `MarkdownMetaExtractor` class, and two methods within the solution:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Screenshot that shows an example of a search for a file by using Visual Studio search.":::

You can also do a "camel case" search. In the following screenshot, a search for *FSS* has found a **F**older**S**ize**S**canner file, class, and method:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Screenshot of an example of a search that uses medial capitals in a text string in Visual Studio search.":::

### Keyboard shortcuts for search results

The search results include tabs for **All**, **Code**, **Visual Studio**. You can save time by using the following keyboard shortcuts for different types of searches:

- **Ctrl**+**Q**, **Ctrl**+**T** for files, types, and members
- **Ctrl**+**Q**, **Ctrl**+**M** for Visual Studio menus, options, components, and templates
- **Ctrl**+**Q**, **Ctrl**+**E** to go to the **All** tab, for both

## Related content

- [Visual Studio commands](reference/visual-studio-commands.md)
- [Keyboard shortcuts in Visual Studio](default-keyboard-shortcuts-in-visual-studio.md)