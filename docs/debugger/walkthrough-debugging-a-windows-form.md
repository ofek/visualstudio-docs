---
title: "Debugging a Windows Form"
description: Follow a walkthrough to see how to create and debug a Windows Form, a common managed application. You can use C#, Visual Basic, or C++.
ms.date: "11/04/2016"
ms.topic: "conceptual"
dev_langs:
  - "CSharp"
  - "VB"
  - "C++"
helpviewer_keywords:
  - "debugging [Visual Studio], walkthroughs"
  - "debugging managed code, Windows Forms"
  - "debugging [Visual Studio], Windows Forms"
  - "Attach to Process dialog box"
  - "debugger, attaching to programs"
  - "Attach to Process dialog box, walkthroughs"
  - "Windows Forms, debugging"
  - "debugging Windows Forms, walkthroughs"
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
---
# Walkthrough: Debugging a Windows Form

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
A Windows Form is one of the most common managed applications. A Windows Form creates a standard Windows application. You can complete this walkthrough using Visual Basic, C#, or C++.

 First, you must close any open solutions.

### To prepare for this walkthrough

- If you already have an open solution open, close it. (On the **File** menu, select **Close Solution**.)

## Create a New Windows Form
 Next, you will create a new Windows Form.

#### To create the Windows form for this walkthrough

1. On the **File** menu, choose **New** and click **Project**.

     The **New Project** dialog box appears.

2. In the Project Types pane, open the **Visual Basic**, **Visual C#**, or **Visual C++** node, then

    1. For Visual Basic or Visual C#, select **Windows Desktop** > **Windows Form App**.

    2. For Visual C++, select **Windows Desktop Application**.

3. In the **Name** box, give the project a unique name (for example, Walkthrough_SimpleDebug).

4. Click **OK**.

     Visual Studio creates a new project and displays a new form in the Windows Forms designer. For more information, see [Windows Forms Designer](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. On the **View** menu, select **Toolbox**.

     The Toolbox opens. For more information, see [Toolbox](../ide/reference/toolbox.md).

6. In the Toolbox, click on the **Button** control and drag the control to the Form design surface. Drop the button on the form.

7. In the Toolbox, click on the **TextBox** control and drag the control to the Form design surface. Drop the **TextBox** on the form.

8. On the form design surface, double-click the button.

     This takes you to the code page. The cursor should be in `button1_Click`.

10. In the function `button1_Click`., add the following code:

    ### [C#](#tab/csharp)
    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ### [VB](#tab/vb)
    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ### [C++](#tab/cpp)
    ```cpp
    textBox1->Text = "Button was clicked!";
    ```
    ---

11. On the **Build** menu, select **Build Solution**.

     The project should build with no errors.

## Debug Your Form
 Now, you are ready to begin debugging.

#### To debug the Windows Form created for this walkthrough

1. In the source window, click the left margin on the same line as the text you added:

    ### [C#](#tab/csharp)
    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

     ### [VB](#tab/vb)
     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ### [C++](#tab/cpp)
    ```cpp
    textBox1->Text = "Button was clicked!";
    ```
    ---

     A red dot appears and the text on the line is highlighted in red. The red dot represents a breakpoint. For more information, see [Breakpoints](/previous-versions/ktf38f66(v=vs.100)). When you run the application under the debugger, the debugger will break execution at that location when the code is hit. You can then view the state of your application and debug it.

    > [!NOTE]
    > You can also right-click any line of code, point to **Breakpoint**, and then click **Insert Breakpoint** to add a breakpoint on that line.

2. ON the **Debug** menu, choose **Start**.

     The Windows Form starts running.

3. On the Windows Form, click the button you added.

     In Visual Studio, this takes you to the line where you set your breakpoint on the code page. This line should be highlighted in yellow. You can now view the variables in your application and control its execution. Your application has now stopped executing, waiting for an action from you.

4. On the **Debug** menu, choose **Windows**, then **Watch**, and click **Watch1**.

5. In the **Watch1** window, click on a blank row. In the **Name** column, type `textBox1.Text` (if you are using Visual Basic or Visual C#) or `textBox1->Text` (if you are using C++), then press ENTER.

     The **Watch1** window shows the value of this variable in quotation marks as:

    `""`

6. On the **Debug** menu, choose **Step Into**.

     The value of textBox1.Text changes in the **Watch1** window to:

    `Button was clicked!`

7. On the **Debug** menu, choose **Continue** to resume debugging your program.

8. On the Windows Form, click the button again.

     Visual Studio breaks execution again.

9. Click on the red dot that represents the breakpoint.

     This removes the breakpoint from your code.

10. On the **Debug** menu, choose **Stop Debugging**.

## Attach to Your Windows Form Application for Debugging
 In Visual Studio, you can attach the debugger to a running process. If you are using an Express Edition, this feature is not supported.

#### To attach to the Windows Form Application for debugging

1. In the project you created above, click in the left margin to once again set a breakpoint at the line you added:

    ### [VB](#tab/vb)
    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ### [C#](#tab/csharp)
    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ### [C++](#tab/cpp)
    ```cpp
    textBox1->Text = "Button was clicked!";
    ```
    ---

2. On the **Debug** menu, select **Start Without Debugging**.

     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.

3. On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)

     The **Attach to Process** dialog box appears.

4. In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.

5. Click the **Attach** button.

6. In your Windows Form, click the one and only button.

     The debugger breaks execution of the Windows Form at the breakpoint.

## Related content
- [Debugging Managed Code](../debugger/debugging-managed-code.md)
- [Debugger Security](../debugger/debugger-security.md)