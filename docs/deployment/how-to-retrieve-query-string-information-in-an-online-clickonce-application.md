---
title: Retrieve query string info in online ClickOnce app
description: Learn how a ClickOnce application can read the query portion of a URL and how to use MageUI to configure your application to accept query string parameters.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs: 
  - VB
  - CSharp
  - C++
helpviewer_keywords: 
  - ClickOnce deployment, query strings
  - query strings, retrieving information
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
---
# Retrieve query string information in an online ClickOnce application

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
The *query string* is the portion of a URL beginning with a question mark (?) that contains arbitrary information in the form *name=value*. Suppose you have a ClickOnce application named `WindowsApp1` that you host on `servername`, and you want to pass in a value for the variable `username` when the application launches. Your URL might look like the following:

 `http://servername/WindowsApp1.application?username=joeuser`

 The following two procedures show how to use a ClickOnce application to obtain query string information.

> [!NOTE]
> You can only pass information in a query string when your application is being launched using HTTP, instead of using a file share or the local file system.

 The first procedure shows how your ClickOnce application can use a small piece of code to read these values when the application launches.

 The next procedure shows how to configure your ClickOnce application using MageUI.exe so that it can accept query string parameters. You will need to do this whenever you publish your application.

> [!NOTE]
> See the "Security" section later in this topic before you make a decision to enable this feature.

 For information about how to create a ClickOnce deployment using *Mage.exe* or *MageUI.exe*, see [Walkthrough: Manually deploy a ClickOnce application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

> [!NOTE]
> Starting in .NET Framework 3.5 SP1, it is possible to pass command-line arguments to an offline ClickOnce application. If you want to supply arguments to the application, you can pass in parameters to the shortcut file with the .APPREF-MS extension.

### To obtain query string information from a ClickOnce application

1. Place the following code in your project. In order for this code to function, you will have to have a reference to System.Web and add `using` or `Imports` directives for System.Web, System.Collections.Specialized, and System.Deployment.Application.

    [!INCLUDE[ndptecclick](../deployment/includes/dotnet-support-application-deployment-api.md)]

    ### [C#](#tab/csharp)
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs" id="Snippet1":::

    ### [VB](#tab/vb)
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb" id="Snippet1":::
    ---

2. Call the function defined previously to retrieve a <xref:System.Collections.DictionaryBase.Dictionary%2A> of the query string parameters, indexed by name.

### To enable query string passing in a ClickOnce application with MageUI.exe

1. Open the .NET Command Prompt and type:

   ```cmd
   MageUI
   ```

2. From the **File** menu, select **Open**, and open the deployment manifest for your ClickOnce application, which is the file ending in the `.application` extension.

3. Select the **Deployment Options** panel in the left-hand navigation window, and select the **Allow URL parameters to be passed to application** check box.

4. From the **File** menu, select **Save**.

> [!NOTE]
> Alternately, you can enable query string passing in Visual Studio. Select the **Allow URL parameters to be passed to application** check box, which can be found by opening the **Project Properties**, selecting the **Publish** tab, clicking the **Options** button, and then selecting **Manifests**.

[!INCLUDE[ndptecclick](../deployment/includes/dotnet-publish-tool.md)]

## Robust programming
 When you use query string parameters, you must give careful consideration to how your application is installed and activated. If your application is configured to install on the user's computer from the Web or from a network share, it is likely that the user will activate the application only once through the URL. After that, the user will usually activate your application using the shortcut in the **Start** menu. As a result, your application is guaranteed to receive query string arguments only once during its lifetime. If you choose to store these arguments on the user's machine for future use, you are responsible for storing them in a safe and secure manner.

 If your application is online only, it will always be activated through a URL. Even in this case, however, your application must be written to function properly if the query string parameters are missing or corrupted.

## .NET Framework security
 Allow passing URL parameters to your ClickOnce application only if you plan to cleanse the input of any malicious characters before using it. A string embedded with quotes, slashes, or semicolons, for example, might perform arbitrary data operations if used unfiltered in a SQL query against a database. For more information on query string security, see [Script exploits overview](/previous-versions/w1sw53ds(v=vs.140)).

## Related content
- [Secure ClickOnce applications](../deployment/securing-clickonce-applications.md)