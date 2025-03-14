---
title: Analyze memory usage in the Performance Profiler
description: Learn how to use the Memory Usage tool without the debugger in the Visual Studio Performance Profiler to monitor your app's memory use.
ms.date: 02/22/2023
ms.topic: how-to
dev_langs: 
  - CSharp
  - VB
  - FSharp
  - C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
---
# Analyze memory usage without debugging in the Performance Profiler (C#, Visual Basic, C++, F#)

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

The **Memory Usage** tool monitors your app's memory use. You can use the tool to study the real-time memory effects of scenarios you're actively developing in Visual Studio. You can take detailed snapshots of the app's memory states, and compare snapshots to find the root causes of memory issues. The Memory Usage tool is supported on .NET, ASP.NET, C++, or mixed mode (.NET and native) apps.

The Memory Usage tool can run [with or without the debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). In this article, we show how to use the Memory Usage tool without the debugger in the Visual Studio **Performance Profiler**, which is recommended for release builds. For information on choosing the best memory analysis tool for your needs, see [Choose a memory analysis tool](../profiling/analyze-memory-usage.md).

## Memory Usage diagnostic sessions

**To start a Memory Usage diagnostic session:**

1. Open a project in Visual Studio.

   The Memory Usage tool supports .NET, ASP.NET, C++, or mixed mode (.NET and native) apps.

1. In the Debug menu, set the solution configuration to **Release** and select **Local Windows Debugger** (or **Local Machine**) as the deployment target.

1. On the menu bar, select  **Debug** > **Performance Profiler**.

1. Under **Available Tools**, select **Memory Usage**, and then select **Start**.

   ![Start a Memory Usage diagnostic session](../profiling/media/memory-usage-start-diagnostics-session.png "Start a Memory Usage diagnostic session")

### Monitor memory use

When you start a diagnostic session, your app starts, and the **Diagnostic Tools** window displays a timeline graph of your app's memory use.

::: moniker range="<=vs-2019"
![Screenshot of the Diagnostic Tools window in the Visual Studio Performance Profiler showing a timeline graph of the app's memory use.](../profiling/media/memory-usage-report-overview.png "Memory Report Overview")
::: moniker-end

::: moniker range="vs-2022"
![Screenshot of the Diagnostic Tools window in the Visual Studio Performance Profiler showing a timeline graph of the app's memory use.](../profiling/media/memory-usage-report-overview-vs-2022.png "Memory Usage Report Overview")
::: moniker-end

The timeline graph shows memory fluctuations as the app runs. Spikes in the graph usually indicate that some code is collecting or creating data, and then discarding it when the processing is done. Large spikes indicate areas that you can optimize. Main concern is a rise in memory consumption that's not returned. This may indicate inefficient memory use or even a memory leak.

### Take snapshots of app memory states

An app uses a large number of objects, and you might want to concentrate your analysis on one scenario. Or, you may find memory issues to investigate. You can take snapshots during a diagnostic session to capture memory usage at particular moments. It's good to get a baseline snapshot of an app before a memory issue appears. You can take another snapshot after the first occurrence of the problem, and additional snapshots if you can repeat the scenario.

To collect snapshots, select **Take snapshot** when you want to capture the memory data.

### <a name="BKMK_Close_a_monitoring_session"></a> Close the diagnostic session

To stop a monitoring session without creating a report, just close the diagnostic window. To generate a report when you're done collecting or have taken snapshots, select **Stop Collection**.

![Stop Collection](../profiling/media/memory-usage-stop-collection.png "Stop Collection")

If you have trouble collecting or displaying data, see [Troubleshoot profiling errors and fix issues](../profiling/troubleshoot-profiler-errors.md).

## Memory Usage reports

After you stop data collection, the **Memory Usage** tool stops the app and displays the **Memory Usage** overview page.

::: moniker range="<=vs-2019"
![Screenshot of the overview page in the Memory Usage tool in the Visual Studio Performance Profiler, showing a memory usage graph and two snapshot panes.](../profiling/media/memory-usage-report-overview-1.png "Memory Usage overview page")
::: moniker-end

::: moniker range="vs-2022"
![Screenshot of the overview page in the Memory Usage tool in the Visual Studio Performance Profiler, showing a memory usage graph and two snapshot panes.](../profiling/media/memory-usage-report-overview-1-vs-2022.png "Memory Usage overview page")
::: moniker-end

### <a name="BKMK_Memory_Usage_snapshot_views"></a> Memory Usage snapshots

The numbers in the **Snapshot** panes show the objects and bytes in memory when each snapshot was taken, and the difference between the snapshot and the previous one.

The numbers are links that open detailed **Memory Usage** report views in new Visual Studio windows. A [snapshot details report](#snapshot-details-reports) shows the types and instances in one snapshot. A [snapshot difference (diff) report](#snapshot-difference-diff-reports) compares the types and instances in two snapshots.

::: moniker range="<=vs-2019"
  ![Snapshot view links](../profiling/media/memory-usage-snapshot-view-numbered.png "Snapshot view links")

|Image|Description|
|-|-|
|![Step 1](../profiling/media/process-guide-1.png "Process Guide-1")|The total number of bytes in memory when the snapshot was taken. Select this link to display a snapshot details report sorted by the total size of the type instances.|
|![Step 2](../profiling/media/process-guide-2.png "Process Guide-2")|The total number of objects in memory when the snapshot was taken. Select this link to display a snapshot details report sorted by the count of instances of the types.|
|![Step 3](../profiling/media/process-guide-3.png "Process Guide-3")|The difference between the total size of memory objects in this snapshot and the previous snapshot. A positive number means the memory size of this snapshot is larger than the previous one, and a negative number means the size is smaller. **Baseline** means a snapshot is the first in a diagnostic session. **No Difference** means the difference is zero. Select this link to display a snapshot diff report sorted by the difference in the total size of instances of the types.|
|![Step 4](../profiling/media/process-guide-4.png "Process Guide-4")|The difference between the total number of memory objects in this snapshot and the previous snapshot. Select this link to display a snapshot diff report. It’s sorted by the difference in the total count of instances of the types.|
::: moniker-end

::: moniker range="vs-2022"
  ![Snapshot view links](../profiling/media/memory-usage-snapshot-view-numbered-vs-2022.png "Snapshot view links")

|Image|Description|
|-|-|
|![Step 1](../profiling/media/process-guide-1.png "Process Guide-1")|The total number of objects in memory when the snapshot was taken. Select this link to display a snapshot details report sorted by the count of instances of the types.|
|![Step 2](../profiling/media/process-guide-2.png "Process Guide-2")|The difference between the total number of memory objects in this snapshot and the previous snapshot. Select this link to display a snapshot diff report sorted by the difference in the total count of instances of the types.|
|![Step 3](../profiling/media/process-guide-3.png "Process Guide-3")|The total number of bytes in memory when the snapshot was taken.Select this link to display a snapshot details report sorted by the total size of the type instances.|
|![Step 4](../profiling/media/process-guide-4.png "Process Guide-4")|The difference between the total size of memory objects in this snapshot and the previous snapshot. A positive number means the memory size of this snapshot is larger than the previous one, and a negative number means the size is smaller. **Baseline** means a snapshot is the first in a diagnostic session. **No Difference** means the difference is zero. Select this link to display a snapshot diff report sorted by the difference in the total size of instances of the types.|
::: moniker-end

## Memory Usage snapshot reports

<a name="BKMK_Snapshot_report_trees"></a> When you select one of the snapshot links in the **Memory Usage** overview page, a snapshot report opens in a new page.

::: moniker range="<=vs-2019"
![Memory Usage snapshot report](../profiling/media/memory-usage-snapshot-report-all.png "Memory Usage snapshot report")
::: moniker-end

::: moniker range="vs-2022"
![Memory Usage snapshot report](../profiling/media/memory-usage-snapshot-report-all-vs-2022.png "Memory Usage snapshot report")
::: moniker-end

If an **Object Type** is blue, you can select it to navigate to the object in the source code, in a separate window.

Types that you can't identify or whose involvement in your code you don't understand are probably .NET, operating system, or compiler objects. The **Memory Usage** tool displays these objects if they're involved in the ownership chains of your objects.

In the snapshot report:

- The **Managed Memory** tree shows the types and instances in the report. Selecting a type or instance displays the **Paths to Root** and **Referenced Objects** trees for the selected item.

- The **Paths to Root** tree shows the chain of objects that reference a type or instance. The .NET garbage collector cleans up the memory for an object only when all references to it have been released.

- The **Referenced Types** or **Referenced Objects** tree shows the objects that the selected type or instance references.

### <a name="BKMK_Report_tree_filters_"></a> Report tree filters

Many types in apps aren't required to app developers. The snapshot report filters can hide most of these types in the **Managed Memory** and **Paths to Root** trees.

::: moniker range="<=vs-2019"
![Sort and filter options](../profiling/media/memory-usage-sort-and-filter.png "Memory Usage Sort and Filter")
::: moniker-end

::: moniker range="vs-2022"
![Sort and filter options](../profiling/media/memory-usage-sort-and-filter-vs-2022.png "Memory usage sort and filter")
::: moniker-end

- <a name="BKMK_Filter"></a> To filter a tree by type name, enter the name in the **Filter** box. The filter isn't case-sensitive, and it recognizes the specified string in any part of the type name.

- <a name="BKMK_Collapse_Small_Objects"></a> Select **Collapse Small Objects** in the **Filter** dropdown to hide types whose **Size (Bytes)** is less than 0.5 percent of the total memory.

- <a name="BKMK_Just_My_Code"></a> Select **Just My Code** in the **Filter** dropdown to hide most instances that are generated by external code. External types belong to the operating system or framework components, or are generated by the compiler.

## Snapshot details reports

 A snapshot details report describes one snapshot from a diagnostic session. To open the report, select the size or objects link in a snapshot pane.

::: moniker range="<=vs-2019"
 ![Links to snapshot report in a snapshot pane](../profiling/media/memory-usage-snapshot-view-snapshot-details-links.png "Links to snapshot report in a snapshot pane")
::: moniker-end

::: moniker range="vs-2022"
 ![Links to snapshot report in a snapshot pane](../profiling/media/memory-usage-snapshot-view-snapshot-details-links-vs-2022.png "Links to snapshot report in a snapshot pane")
::: moniker-end

Both links open the same report. The only difference is the starting sort order of the **Managed Memory** tree. The size link sorts the report by the **Inclusive Size (Bytes)** column. The objects link sorts the report by the **Count** column. You can change the sort column or order after the report opens.

### <a name="BKMK_Managed_Memory_tree__Snapshot_details_"></a> Managed Memory tree (Snapshot details reports)

 The **Managed Memory** tree lists the types of objects that are held in memory. Expand a type name to view the 10 largest instances of the type, sorted by size. Select a type or instance to display the **Paths to Root** and **Referenced Objects** trees for the selected item.

::: moniker range="<=vs-2019"
 ![Managed Heap tree](../profiling/media/memory-usage-snapshot-details-managed-heap-tree.png "Managed Heap tree")
::: moniker-end

::: moniker range="vs-2022"
 ![Managed Memory tree](../profiling/media/memory-usage-snapshot-details-managed-heap-tree-vs-2022.png "Managed Memory tree")
::: moniker-end

The **Managed Memory** tree in a snapshot details report has the following columns:

|Name|Description|
|-|-|
|**Object Type**|The name of the type or object instance.|
|**Count**|The number of object instances of the type. **Count**  is always 1 for an instance.|
|**Size (Bytes)**|For a type, the size of all instances of the type in the snapshot, less the size of objects contained in the instances.For an instance, the size of the object, less the size of objects contained in the instance. |
|**Inclusive Size (Bytes)**|The size of the instances of the type, or the size of a single instance, including the size of contained objects.|
|**Module**|The module that contains the object.|

### <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Paths to Root tree (Snapshot details reports)

The **Paths to Root tree** shows the chain of objects that reference a type or instance. The .NET garbage collector cleans up the memory for an object only when all references to it have been released.

For a type in the **Paths to Root** tree, the number of objects that hold references to that type appears in the **Reference Count** column.

::: moniker range="<=vs-2019"
![Paths to Root tree for types](../profiling/media/memory-usage-snapshot-details-type-paths-to-root-tree.png "Paths to Root tree for types")
::: moniker-end

::: moniker range="vs-2022"
![Paths to Root tree for types](../profiling/media/memory-usage-snapshot-details-type-paths-to-root-tree-vs-2022.png "Paths to Root tree for types")
::: moniker-end

### <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Referenced Types or Referenced Objects tree (Snapshot details reports)

The **Referenced Types** or **Referenced Objects** tree shows the objects that the selected type or instance references.

::: moniker range="<=vs-2019"
![Referenced Objects tree for instances](../profiling/media/memory-usage-snapshot-details-referenced-objects-instance.png "Referenced Objects tree for instances")
::: moniker-end

::: moniker range="vs-2022"
![Referenced Objects tree for instances](../profiling/media/memory-usage-snapshot-details-referenced-objects-instance-vs-2022.png "Referenced Objects tree for instances")
::: moniker-end

A **Referenced Types** tree in a snapshot details report has the following columns. A **Referenced Objects** tree doesn't have the **Reference Count** column.

|Name|Description|
|-|-|
|**Object Type** or **Instance**|The name of the type or instance.|
|**Reference Count**|For types, the number of object instances of the type.|
|**Size (Bytes)**|For a type, the size of all instances of the type, less the size of objects contained in the type. For an instance, the size of the object, less the size of objects contained in the object.|
|**Inclusive Size (Bytes)**|The total size of the instances of the type, or the size of the instance, including the size of contained objects.|
|**Module**|The module that contains the object.|

## Snapshot difference (diff) reports

A snapshot difference (diff) report shows the changes between a primary snapshot and the preceding snapshot. To open a diff report, select one of the difference links in a snapshot pane.

Both links open the same report. The only difference is the starting sort order of the **Managed Memory** tree in the report. The size link sorts the report by the **Inclusive Size Diff (Bytes)** column. The objects link sorts the report by the **Count Diff** column. You can change the sort column or order after the report opens.

::: moniker range="<=vs-2019"
 ![Links to difference report in a snapshot pane](../profiling/media/memory-usage-snapshot-view-snapshot-diff-links.png "Links to difference report in a snapshot pane")
::: moniker-end

::: moniker range="vs-2022"
 ![Links to difference report in a snapshot pane](../profiling/media/memory-usage-snapshot-view-snapshot-diff-links-vs-2022.png "Links to difference report in a snapshot pane")
::: moniker-end

### <a name="BKMK_Managed_Memory_tree__Snapshot_diff_"></a> Managed Memory tree (Snapshot diff reports)

 The **Managed Memory** tree lists the types of objects that are held in memory. You can expand a type name to view the 10 largest instances of the type, sorted by size. Select a type or instance to display the **Paths to Root** and **Referenced Objects** trees for the selected item.

::: moniker range="<=vs-2019"
 ![Managed Heap tree for a type in difference report](../profiling/media/memory-usage-snapshot-diff-type-heap.png "Managed Heap tree for a type in difference report")
::: moniker-end

::: moniker range="vs-2022"
 ![Managed Memory tree for a type in difference report](../profiling/media/memory-usage-snapshot-diff-type-heap-vs-2022.png "Managed Memory tree for a type in difference report")
::: moniker-end

The **Managed Memory** tree in a snapshot diff report has the following columns:

|Name|Description|
|-|-|
|**Object Type**|The name of the type or object instance.|
|**Count**|The number of instances of a type in the primary snapshot. **Count** is always 1 for an instance.|
|**Count Diff**|For a type, the difference in the number of instances of the type between the primary snapshot and the previous snapshot. The field is blank for an instance.|
|**Size (Bytes)**|The size of the objects in the primary snapshot, less the size of objects in the objects. For a type, **Size (Bytes)** and **Inclusive Size (Bytes)** are the totals of the sizes of the type instances.|
|**Total Size Diff (Bytes)**|For a type, the difference in the total size of instances of the type between the primary snapshot and the previous snapshot, less the size of objects in the instances. The field is blank for an instance.|
|**Inclusive Size (Bytes)**|The size of the objects in the primary snapshot, including the size of objects in the objects.|
|**Inclusive Size Diff (Bytes)**|For a type, the difference in the size of all instances of the type between the primary snapshot and the previous snapshot, including the size of objects in the objects. The field is blank for an instance.|
|**Module**|The module that contains the object.|

### <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Paths to Root tree (Snapshot diff reports)

The **Paths to Root tree** shows the chain of objects that reference a type or instance. The .NET garbage collector cleans up the memory for an object only when all references to it have been released.

For a type in the **Paths to Root** tree, the number of objects that hold references to that type appears in the **Reference Count** column. The difference in count from the previous snapshot is in the **Reference Diff** column.

::: moniker range="<=vs-2019"
 ![Paths To Root tree in a diff report](../profiling/media/memory-usage-snapshot-diff-paths-to-root-instance-all.png "Paths To Root tree in a diff report")
::: moniker-end

::: moniker range="vs-2022"
 ![Paths To Root tree in a diff report](../profiling/media/memory-usage-snapshot-diff-paths-to-root-instance-all-vs-2022.png "Paths To Root tree in a diff report")
::: moniker-end

### <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Referenced Types or Referenced Objects tree (Snapshot diff reports)

The **Referenced Types** or **Referenced Objects** tree shows the objects that the selected type or instance references.

::: moniker range="<=vs-2019"
![Referenced Types in a diff report](../profiling/media/memory-usage-snapshot-diff-referenced-types.png "Referenced Types in a diff report")
::: moniker-end

::: moniker range="vs-2022"
![Referenced Types in a diff report](../profiling/media/memory-usage-snapshot-diff-referenced-types-vs-2022.png "Referenced Types in a diff report")
::: moniker-end

A **Referenced Types** tree in a snapshot diff report has the following columns. A **Referenced Objects** tree has the **Instance**, **Size (Bytes)**, **Inclusive Size (Bytes)**, and **Module** columns.

|Name|Description|
|-|-|
|**Object Type** or **Instance**|The name of the type or object instance.|
|**Reference Count**|The number of instances of a type in the primary snapshot.|
|**Reference Count Diff**|For a type, the difference in the number of instances of the type between the primary snapshot and the previous snapshot.|
|**Size (Bytes)**|The size of the objects in the primary snapshot, less the size of objects in the objects. For a type, **Size (Bytes)** and **Inclusive Size (Bytes)** are the totals of the sizes of the type instances.|
|**Total Size Diff (Bytes)**|For a type, the difference in the total size of instances of the type between the primary snapshot and the previous snapshot, less the size of objects in the instances. |
|**Inclusive Size (Bytes)**|The size of the objects in the primary snapshot, including the size of objects in the objects.|
|**Inclusive Size Diff (Bytes)**|For a type, the difference in the size of all instances of the type between the primary snapshot and the previous snapshot, including the size of objects in the objects.|
|**Module**|The module that contains the object.|

## Related content

- [Profiling in Visual Studio](../profiling/index.yml)
- [First look at profiling tools](../profiling/profiling-feature-tour.md)
- [Performance best practices for UWP apps using C++, C#, and Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnosing memory issues with the new Memory Usage tool in Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)
