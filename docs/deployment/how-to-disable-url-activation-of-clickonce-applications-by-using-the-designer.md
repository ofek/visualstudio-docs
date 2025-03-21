---
title: Disable URL activation of ClickOnce apps using Designer
description: Learn how to disable automatic start on install for a ClickOnce application using Visual Studio, so that users must start the application from the Start menu.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs: 
  - VB
  - CSharp
  - C++
helpviewer_keywords: 
  - disallowURLActivation
  - URL activation, ClickOnce applications
  - ClickOnce deployment, URL activation
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
---
# Disable URL activation of ClickOnce applications by using the Designer

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Typically, a ClickOnce application will start automatically immediately after it is installed from a Web server. For security reasons, you may decide to disable this behavior, and tell users to start the application from the **Start** menu instead. The following procedure describes how to disable URL activation.

 This technique can be used only for ClickOnce applications installed on the user's computer from a Web server. It cannot be used for online-only applications, which can be started only by using their URL. For more information about the difference between online-only and installed applications, see [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).

 This procedure uses Visual Studio. You can also accomplish this task by using the Windows Software Development Kit (SDK). For more information, see [How to: Disable URL Activation of ClickOnce Applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## Procedure

#### To disable URL activation for your application

1. Right-click your project name in **Solution Explorer**, and click **Properties**.

2. On the **Properties** page, click the **Publish** tab.

   [!INCLUDE[ndptecclick](../deployment/includes/dotnet-publish-tool.md)]

3. Click **Options**.

4. Click **Manifests**.

5. Select the check box labeled **Block application from being activated via a URL**.

6. Deploy your application.

## Related content
- [Publishing ClickOnce applications](../deployment/publishing-clickonce-applications.md)