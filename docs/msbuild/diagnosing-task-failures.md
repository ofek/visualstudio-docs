---
title: Diagnose MSBuild task failures
description: Diagnose MSBuild task failures by identifying the failing task, the tool name, and other information for troubleshooting.
ms.date: 03/14/2023
ms.topic: how-to
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
---
# Diagnose MSBuild task failures

`MSB6006` is emitted when a <xref:Microsoft.Build.Utilities.ToolTask>–derived class runs a tool process that returns a nonzero exit code if the task did not log a more specific error.

## Identify the failing task

When you encounter a task error, the first step is to identify the task that is failing.

The text of the error specifies the tool name (either a friendly name provided by the task's implementation of <xref:Microsoft.Build.Utilities.ToolTask.ToolName> or the name of the executable) and the numeric exit code. For example, in `error MSB6006: "custom tool" exited with code 1.` the tool name is `custom tool` and the exit code is `1`.

**To find the failed MSBuild task:**

+ **In the command-line builds**:  If the build was configured to include a summary (the default), the summary will look like this:

  ```text
  Build FAILED.

  "S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
  (InvokeToolTask target) ->
    S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
  ```

  This result indicates that the error occurred in a task defined on line 19 of the file `S:\MSB6006_demo\MSB6006_demo.csproj`, in a target named `InvokeToolTask`, in the project `S:\MSB6006_demo\MSB6006_demo.csproj`.

+ **In the Visual Studio UI**: The same information is available in the Visual Studio error list in the columns `Project`, `File`, and `Line`.

## Find more failure information

Error MSB6006 is emitted when the task did not log a specific error. The failure to log an error is often because the task is not configured to understand the error format emitted by the tool it calls.

Well-behaved tools generally emit some contextual or error information to their standard output or error stream, and tasks capture and log this information by default. Look in the log entries before the error occurred for additional information. Rerunning the build with a higher log level may be required to preserve this information. Hopefully, the additional context or errors identified in logging reveal the root cause of the problem. If not, you may have to narrow down the potential causes by examining the properties and items that are inputs to the failing task.

> [!NOTE]
> MSBuild recognizes a specific diagnostic output format. The details of this format are documented at [MSBuild and Visual Studio format for diagnostic messages](msbuild-diagnostic-format-for-tasks.md).
