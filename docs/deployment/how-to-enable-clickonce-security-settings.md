---
title: Enable & configure ClickOnce security
description: Learn how the Publish wizard automatically enables code access security for ClickOnce applications to publish the application.
ms.date: 08/04/2023
ms.topic: how-to
dev_langs: 
  - VB
  - CSharp
  - C++
helpviewer_keywords: 
  - security [Visual Studio], ClickOnce applications
  - ClickOnce deployment, security settings
  - security settings, ClickOnce deployment
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
---
# Enable and configure ClickOnce security settings in Visual Studio

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

You can enable and configure ClickOnce security settings in the **Security** page of the **Project Designer**. In this article, you learn how to enable security settings, configure security zones, and configure customized security zones.

 [!INCLUDE[ndptecclick](../deployment/includes/dotnet-task-unsupported.md)]

## Enable ClickOnce security settings

Code access security for ClickOnce applications must be enabled in order to publish the application. This is done automatically when you publish an application using the Publish wizard.

In some cases, enabling code access security can impact performance when building or debugging your application; in these cases, you may wish to temporarily disable the security settings.

ClickOnce security settings can be enabled or disabled on the **Security** page of the **Project Designer**.

1. With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.

2. Click the **Security** tab.

3. Select the **Enable ClickOnce Security Settings** check box.

     You can now customize the security settings for your application on the Security page.

    > [!NOTE]
    > This check box is automatically selected each time the application is published with the **Publish** wizard.

### To disable ClickOnce security settings

1. With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.

2. Click the **Security** tab.

3. Clear the **Enable ClickOnce Security Settings** check box.

     Your application will be run with the full trust security settings; any settings on the **Security** page will be ignored.

    > [!NOTE]
    > Each time the application is published with the Publish wizard, this check box will be selected; you must clear it again after each successful publish.

## Set a security zone for a ClickOnce application

When setting code access security permissions for a ClickOnce application, you need to start with a base set of permissions on the **Security** page of the **Project Designer**.

In most cases, you can also choose the **Internet** zone which contains a limited set of permissions, or the **Local Intranet** zone which contains a greater set of permissions. If your application requires custom permissions, you can do so by choosing the [Custom security zone](#set-custom-permissions-for-a-clickonce-application).

### To set a security zone

1. With a project selected in **Solution Explorer**, on the **Project** menu click **Properties**.

2. Click the **Security** tab.

3. Select the **Enable ClickOnce Security Settings** check box.

4. Select the **This is a partial trust application** option button.

     The controls in the **ClickOnce security permissions** section are enabled.

5. In the **Zone your application will be installed from** drop-down list, select a security zone.

## Set custom permissions for a ClickOnce application

You can deploy a ClickOnce application that uses default permissions for the Internet or Local Intranet zones. Alternatively, you can create a custom zone for the specific permissions that the application needs. You can do this by customizing the security permissions on the **Security** page of the **Project Designer**.

### To customize a permission

1. With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.

2. Click the **Security** tab.

3. Select the **Enable ClickOnce Security Settings** check box.

4. Select the **This is a partial trust application** option button.

     The controls in the **ClickOnce security permissions** section are enabled.

5. From the **Zone your application will be installed from** drop-down list, click **(Custom)**.

6. Click **Edit Permissions XML**.

     The *app.manifest* file opens in the XML Editor.

7. Before the `</applicationRequestMinimum>` element, add XML code for permissions that your application requires.

    > [!NOTE]
    > You can use the `ToXml` method of a permission set to generate the XML code for the application manifest. For example, to generate the XML for the <xref:System.Security.Permissions.EnvironmentPermission> permission set, call the <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> method.

## Related content

- [Secure ClickOnce applications](../deployment/securing-clickonce-applications.md)
- [Code access security for ClickOnce applications](../deployment/code-access-security-for-clickonce-applications.md)
