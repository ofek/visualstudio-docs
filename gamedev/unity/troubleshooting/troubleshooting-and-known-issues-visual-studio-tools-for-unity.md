---
title: Troubleshoot Visual Studio Tools for Unity
description: Troubleshoot Visual Studio Tools for Unity, review known issues and solutions for connections, program execution, project compatibility, debugging, and IntelliSense.
ms.date: "04/04/2022"
ms.technology: vs-unity-tools
ms.prod: visual-studio
ms.topic: troubleshooting
author: therealjohn
ms.author: johmil
manager: crdun
---
# Troubleshooting and known issues (Visual Studio Tools for Unity)

In this section, you'll find solutions to common issues with Visual Studio Tools for Unity, descriptions of known issues, and learn how you can help improve Visual Studio Tools for Unity by reporting errors.

## Troubleshooting the connection between Unity and Visual Studio

### Confirm `Editor Attaching` is enabled or `Code Optimization On Startup` is set to `Debug`

In the Unity Menu, select `Edit / Preferences`.

Depending on the Unity version used :
- Confirm that `Code Optimization On Startup` is set to `Debug`.
- Or select the `External Tools` tab. Confirm that the `Editor Attaching` checkbox is enabled. 

For more information, see the [Unity Preferences documentation](https://docs.unity3d.com/Manual/Preferences.html).

### Unable to attach

- Try to temporarily disable your antivirus or create exclusion rules for both VS and Unity.
- Try to temporarily disable your firewall or create rules for allowing TCP/UDP networking between VS and Unity.
- Some programs, like Team Viewer, can interfere with process detection. You can try to temporarily stop any extra software to see if it changes something.
- Do not rename the main Unity executable, as VSTU is only monitoring "Unity.exe" processes.

## Visual Studio crashes

This issue can be due to the Visual Studio MEF cache being corrupted.

Try removing the following folder to reset the MEF cache (close Visual Studio before doing this):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

This should fix your issue. In case you are still experiencing the problem, run a Developer Command Prompt for Visual Studio as Administrator and use the following command:

```batch
 devenv /setup
```

## Visual Studio stops responding

Several Unity plugins like Parse, FMOD, UMP (Universal Media Player), ZFBrowser, or Embedded Browser are using native threads. It’s an issue when a plugin ends up attaching a native thread to the runtime, which then does blocking calls to the OS. This means Unity can't interrupt that thread for the debugger (or domain reload) and stop responding.

For FMOD, there is a workaround, you can pass `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` initialization [flag](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) to disable asynchronous processing and perform all processing on the main thread.

If you are developing your own native plugin, We recommend using *asynchronous procedure calls* ([APC](/windows/win32/sync/asynchronous-procedure-calls)) and especially `SleepEx`, `SignalObjectAndWait`, `MsgWaitForMultipleObjectsEx`, `WaitForMultipleObjectsEx`, or `WaitForSingleObjectEx` functions to properly cooperate with Unity and Mono when the debugger needs to suspend threads.

## Incompatible project in Visual Studio

The very important thing to know is that Visual Studio is saving the “Incompatible” state in project settings and will not try to reload a project until you explicitly use `Reload Project`. So, after each troubleshooting step, make sure you try to re-open the solution and try to right-click on all incompatible projects and choose `Reload Project`.

1. Check that Visual Studio is set as your external script editor in Unity using `Edit / Preferences / External Tools`.
2. Depending on your Unity version:
   - Check that the Visual Studio plugin is installed in Unity. `Help / About` should display a message like Microsoft Visual Studio Tools for Unity is enabled at the bottom.
   - Unity 2020.x+: Check that you are using the latest Visual Studio Editor package in `Window / Package Manager`.
3. Try deleting all projects/solution files and the `.vs` folder in your project.
4. Try recreating projects/solution using `Open C# Project` or `Edit / Preferences / External tools / Regenerate Project files`.
5. Make sure you installed the Game/Unity workload in Visual Studio.
6. Try to clean the MEF cache as explained [here](#visual-studio-crashes).
7. Try to re-install Visual Studio (using the Game/Unity workload only to start).
8. Try to disable third-party extensions in case they could interfere with the Unity extension in `Tools / Extensions`.

## Extra reloads, or Visual Studio losing all open windows

Be sure to never touch project files directly from an asset processor or any other tool. If you really need to manipulate the project file, we expose an API for that. Please check the [Assembly references issues section](#assembly-reference-or-project-property-issues).

If you experience extra reloads or if Visual Studio is losing all open Windows on reload, make sure that you have proper .NET targeting packs installed. Check the following section about frameworks for more information.

## The debugger does not break on exceptions

When using the legacy Unity runtime (.NET 3.5 equivalent), the debugger will always break when an exception is unhandled (=outside a try/catch block). If the exception is handled, the debugger will use the Exception Settings Window to determine if a break is required or not.

With the new runtime (.NET 4.6 equivalent), Unity introduced a new way for managing user exceptions and as a result, all exceptions are seen as "user-handled" even if they are outside a try/catch block. That's why you now need to explicitly check them in the Exception Settings Window if you want the debugger to break.

In the Exception Settings window (Debug > Windows > Exception Settings), expand the node for a category of exceptions (for example, Common Language Runtime Exceptions, meaning .NET exceptions), and select the check box for the specific exception you want to catch within that category (for example System.NullReferenceException). You can also select an entire category of exceptions.

## On Windows, Visual Studio asks to download the Unity target framework

When using the legacy Unity runtime (.NET 3.5 equivalent), Visual Studio Tools for Unity requires the .NET Framework 3.5, which isn't installed by default on Windows 8 or 10. To fix this issue, follow the instructions to download and install the .NET framework 3.5.

When using the new Unity runtime, .NET targeting packs version 4.6 or 4.7.1 are also required depending on the Unity version. It is possible to use the Visual Studio installer to quickly install them (modify your installation, individual components, .NET category, select all 4.x targeting packs).

## Assembly reference or project property issues

If your project is complex reference-wise or if you want to better control this generation step, you can use our [API](../extensibility/customize-project-files-created-by-vstu.md) for manipulating the generated project or solution content. You can also use [response files](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) in your Unity project and we'll process them.

With recent Visual Studio and Unity versions, the best approach seems to use a custom `Directory.Build.props` file along with your generated projects. You will then be able to contribute to the project structure without interfering with the generation process.

## Breakpoints with a warning

If Visual Studio is unable to find a source location for a specific breakpoint you will see a warning around your breakpoint. Check that the script you are using is properly loaded/used in the current Unity scene.

## Breakpoints not hit

Check that the script you are using is properly loaded/used in the current Unity scene. Quit both Visual Studio and Unity then delete all generated files (\*.csproj, \*.sln), the `.vs` folder and the whole Library folder. You can find more information on C# debugging on the Unity [website](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html).

## Unable to debug Android players

We use multicast for player detection (which is the default mechanism used by Unity), but after that we use a regular TCP connection to attach the debugger. The detection phase is the main issue for Android devices.

Wifi is versatile but super slow compared to USB because of latency. We saw a lack of proper multicast support for some routers or devices (Nexus series are well known for this).

USB is super-fast for debugging, and Visual Studio Tools for Unity is now able to detect USB devices, and talk to the adb server to properly forward ports for debugging.

## Issues with IntelliSense or code coloration

Try upgrading your Visual Studio to the latest version. Try the same troubleshooting steps as for [Incompatible projects](#incompatible-project-in-visual-studio).

## Known issues

There are known issues in Visual Studio Tools for Unity that result from how the debugger interacts with Unity's older version of the C# compiler. We're working to help fix these problems, but you might experience the following issues in the meantime:

- When debugging, Unity sometimes crashes.

- When debugging, Unity sometimes freezes.

- Stepping into and out of methods sometimes behaves incorrectly, especially in iterators or within switch statements.

## Report errors

Please help us improve the quality of Visual Studio Tools for Unity by sending error reports when you experience crashing, freezes, or other errors. This helps us investigate and fix problems in Visual Studio Tools for Unity. Thank you!

### How to report an error when Visual Studio freezes

There are reports that Visual Studio sometimes freezes when debugging with Visual Studio Tools for Unity, but we need more data to understand this problem. You can help us investigate by following the steps below.

##### To report that Visual Studio freezes while debugging with Visual Studio Tools for Unity

*On Windows:*

1. Open a new instance of Visual Studio.

1. Open the Attach to Process dialog. In the new instance of Visual Studio, on the main menu, choose **Debug**, **Attach to Process**.

1. Attach the debugger to the frozen instance of Visual Studio. In the **Attach to Process** dialog, select the frozen instance of Visual Studio from the **Available Processes** table, then choose the **Attach** button.

1. Pause the Debugger. In the new instance of Visual Studio, on the main menu, choose **Debug**, **Break All**, or just press **Ctrl+Alt+Break**.

1. Create a thread-dump. In the Command window, enter the following command and press **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    You might need to make the **Command** window visible first. In Visual Studio, on the main menu, choose **View**, **Other Windows**, **Command Window**.

*On Mac:*

1. Open a terminal and get the PID of Visual Studio for Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Launch the lldb debugger:

    ```shell
    lldb
    ```

1. Attach to the Visual Studio for Mac instance using the PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Retrieve the stacktrace for all the threads:

    ```shell
    bt all
    ```

Finally, send the thread-dump to [vstusp@microsoft.com](mailto:vstusp@microsoft.com), along with a description of what you were doing when Visual Studio became frozen.

## See also

- [Visual Studio troubleshooting](/troubleshoot/visualstudio/welcome-visual-studio/)
