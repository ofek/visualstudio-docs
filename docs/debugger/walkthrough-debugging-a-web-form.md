---
title: "Debug a Web Form"
description: Follow a walkthrough to see how to debug an ASP.NET Web application (Web Form), including how to set breakpoints and examine variables.
ms.date: "11/04/2016"
ms.topic: "conceptual"
dev_langs:
  - "CSharp"
  - "VB"
  - "FSharp"
  - "C++"
helpviewer_keywords:
  - "Web pages [.NET Framework], debugging"
  - "Web sites [.NET Framework], debugging"
  - "ASP.NET, debugging Web applications"
  - "Web applications [.NET Framework], debugging"
  - "ASP.NET Web sites, debugging"
  - "ASP.NET Web pages, debugging"
  - "debugging ASP.NET Web applications, Web Forms"
  - "debugging [Visual Studio], Web Forms"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# Walkthrough: Debugging a Web Form

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
The steps in this walkthrough show you how to debug an ASP.NET Web application, also known as a Web Form. It shows you how to start and stop execution, set breakpoints, and examine variables in the **Watch** window.

> [!NOTE]
> To complete this walkthrough, you must have Administrator privileges on the server computer. By default, the ASP.NET process, aspnet_wp.exe or w3wp.exe, runs as an ASP.NET process. To debug ASP.NET, you must have Administrator privileges on the computer where ASP.NET runs it. For more information, see [System Requirements](../debugger/aspnet-debugging-system-requirements.md).

The dialog boxes and menu commands you see might differ from those described in Help, depending on your active settings or edition. To change your settings, choose **Import and Export Settings** on the **Tools** menu. For more information, see [Reset settings](../ide/environment-settings.md#reset-settings).

## To create the Web Form

1. If you already have a solution open, close it.

2. On the **File** menu, click **New**, and then click **Web Site**.

    The **New Web Site** dialog box appears.

3. In the **Templates** pane, click **ASP.NET Web Site**.

4. On the **Location** line, click **HTTP** from the list, and in the text box, type **http://localhost/WebSite**.

5. In the **Language** list, click **Visual C#** or **Visual Basic**.

6. Click **OK**.

    Visual Studio creates a new project, and displays the default HTML source code. It also creates a new virtual directory named **WebSite** under **Default Web Site** in IIS.

7. Click the **Design** tab on the bottom margin.

8. Click the **Toolbox** tab on the left margin, or select it on the **View** menu.

    The **Toolbox** opens.

9. In the **Toolbox**, click the **Button** control and add it to the main design surface, Default.aspx.

10. In the **Toolbox**, click the **Textbox** control, and drag the control to the main design surface, Default.aspx.

11. Double-click the button control you dropped.

     This takes you to the code page: Default.aspx.cs for C# or Default.aspx.vb for Visual Basic. The cursor should be in the function `Button1_Click`.

12. In the `Button1_Click` function, add the following code:

    ### [C#](#tab/csharp)
    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

    ### [VB](#tab/vb)
    ```vb
    TextBox1.Text = "Button was clicked!"
    ```
    ---

13. On the **Build** menu, click **Build Solution**.

     The project should build without errors.

     Now, you are ready to start debugging.

## To debug the Web Form

1. In the Default.aspx.cs or Default.aspx.vb window, click the left margin on the same line as the text you added:

   ### [C#](#tab/csharp)
   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

   ### [VB](#tab/vb)
   ```vb
   TextBox1.Text = "Button was clicked!"
   ```
   ---

    A red dot appears and the text on the line is highlighted in red. The red dot represents a breakpoint. When you run the application under the debugger, the debugger will break execution at that location when the code is hit. You can then view the state of your application and debug it. For more information, see [Breakpoints](/previous-versions/ktf38f66(v=vs.100)).

2. On the **Debug** menu, click **Start Debugging**.

3. The **Debugging Not Enabled** dialog box appears. Select **Modify the Web.config file to enable debugging** option, and click **OK**.

    Internet Explorer starts and displays the page that you just designed.

4. In Internet Explorer, click the button.

    In Visual Studio, this takes you to the line where you set your breakpoint on the code page Default.aspx.cs or Default.aspx.vb. This line should be highlighted in yellow. You can now view the variables in your application and control its execution. Your application stops executing and waits for a command from you.

5. On the **Debug** menu, click **Windows**, then click **Watch**, and then click **Watch1**.

6. In the **Watch** window, type **TextBox1.Text**.

    The **Watch** window shows the value of the variable `TextBox1.Text`:

   '""'

7. On the **Debug** menu, click **Step Over**.

    The value of `TextBox1.Text` changes in the **Watch** window to read:

   `"Button was clicked!"`

8. On the **Debug** menu, click **Continue**.

9. In Internet Explorer, click the button again.

     Execution stops at the breakpoint again.

10. In the Default.aspx.cs or Default.aspx.vb window, click the red dot in the left margin.

     This removes the breakpoint.

11. On the **Debug** menu, click **Stop Debugging**.

## To attach to the Web Form for debugging

1. In Visual Studio, you can attach the debugger to a running process. For most effective debugging, compile the executable as a Debug version with symbol (PDB) files.

2. In the Default.aspx.cs or Default.aspx.vb window, click in the left margin to again set a breakpoint at the line you added:

   ### [C#](#tab/csharp)
   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

   ### [VB](#tab/vb)
   ```vb
   TextBox1.Text = "Button was clicked!"
   ```
   ---

3. On the **Debug** menu, click **Start Without Debugging**.

    The Web Form starts to run under Internet Explorer, but the debugger is not attached.

4. Attach to the ASP.NET process. For more information, see [Debugging Deployed Web Applications](../debugger/debugging-deployed-web-applications.md).

5. In Internet Explorer, click the button on your form.

    In Visual Studio, you should hit the breakpoint in Default.aspx.cs, Default.aspx.vb, or Default.aspx.

6. When you are finished debugging, on the **Debug** menu, click **Stop Debugging**.

## Related content

- [Debug ASP.NET Applications](../debugger/how-to-enable-debugging-for-aspnet-applications.md)