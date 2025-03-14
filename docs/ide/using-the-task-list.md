---
title: Use the Task List to track and use code comments
description: Explore the Task List in Visual Studio and discover how the tool can help you track and use code comments more efficiently.
ms.date: 06/22/2023
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-ide-general
---
# Use the Task List

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

Use **Task List** to track code comments that use tokens such as `TODO` and `HACK`, or custom tokens, and to manage shortcuts that take you directly to a predefined location in code. Select an item in the list to go to its location in the source code.

> [!NOTE]
> This topic applies to Visual Studio on Windows. For Visual Studio for Mac, see [Task comments (Visual Studio for Mac)](/visualstudio/mac/task-comments).

## The Task List window

When **Task List** is open, it appears at the bottom of the application window.

To open **Task List**, select **View** > **Task List**, or from the keyboard press **Ctrl**+**\\**,**T**.

![Screenshot of the Task List window.](media/task-list-window.png)

To change the sort order of the list, select the header of any column. To further refine your search results, press **Shift** and select a second column header. Alternatively, on the shortcut menu, choose **Sort by**, and then choose a header. To further refine your search results, press **Shift** and choose a second header.

To show or hide columns, on the shortcut menu, choose **Show Columns**. Select the columns that you want to show or hide.

To change the order of the columns, drag any column header to the location that you want.

> [!TIP]
> The **Project Rank** column denotes project dependencies. Projects with a rank of 1 do not depend on any other projects. Projects with a rank of 2 depend on one or more projects with a rank of 1, and so on. For more information, see [Standard Table Column Definitions: Project Rank field](/dotnet/api/microsoft.visualstudio.shell.tablecontrol.standardtablecolumndefinitions.projectrank).

## Tokens and comments

A comment in your code preceded by a comment marker and a predefined token also appears in **Task List**. For example, the following C# comment has three distinct parts:

- The comment marker (`//`)

- The token, for example (`TODO`)

- The comment (the rest of the text)

```csharp
// TODO: Load state from previously suspended application
```

Because `TODO` is a predefined token, this comment appears as a `TODO` task in the list.

### Custom tokens

By default, Visual Studio includes the following tokens: `HACK`, `TODO`, `UNDONE`, and `UnresolvedMergeConflict`. They aren't case-sensitive. You can also create your own custom tokens.

> [!NOTE]
> Default tokens are available only for the C/C++, C#, and Visual Basic languages. To create your own tokens for other programming languages, use the following steps.

To create a custom token:

1. On the **Tools** menu, choose **Options**.

2. Open the **Environment** folder and then choose **Task List**.

   The [Task List options page](reference/task-list-environment-options-dialog-box.md) is displayed.

   ![Screenshot of the options available in the Task List dialog box.](media/tools-options-environment-task-list.png)

3. In the **Name** text box, enter your token name, for example **BUG**.

4. In the **Priority** drop-down list, choose a default priority for the new token.

5. Choose **Add**.

   > [!TIP]
   > The **Add** button becomes enabled after you enter a name. You must enter a name before you select **Add**.

## Shortcuts

A *shortcut* is a bookmark in the code that is tracked in **Task List**. It has a different icon than a regular bookmark. Double-click the shortcut in **Task List** to go to the corresponding location in the code.

![Screenshot of an example shortcut that you can bookmark to view in the Task List.](media/task-list-bookmark-shortcut.png)

### Create a shortcut

To create a shortcut, insert the pointer into the code where you want to place a shortcut. Choose **Edit** > **Bookmarks** > **Add Task List Shortcut** or press **Ctrl**+**K**, **Ctrl**+**H**.

To navigate through the shortcuts in the code, choose a shortcut in the list, and then choose **Next Task** or **Previous Task** from the **View** menu. (You can also choose these options from the right-click context menu in the **Task List** window.)

## Related content

- [Task List, Environment, Options dialog box](../ide/reference/task-list-environment-options-dialog-box.md)
- [Task comments (Visual Studio for Mac)](/visualstudio/mac/task-comments)
