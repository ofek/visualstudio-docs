---
title: Specify Start menu name for a ClickOnce app
description: Learn how to change the display name for your ClickOnce application by setting Product name in the Publish Options dialog box.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs: 
  - VB
  - CSharp
  - C++
helpviewer_keywords: 
  - Start menu resource name
  - Start menu name
  - ClickOnce deployment, Start menu name
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
---
# Specify a Start menu name for a ClickOnce application

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
When a ClickOnce application is installed for both online and offline use, an entry is added to the **Start** menu and the **Add or Remove Programs** list. By default, the display name is the same as the name of the application assembly, but you can change the display name by setting **Product name** in the **Publish Options** dialog box.

 **Product name** will be displayed on the *publish.htm* page; for an installed offline application, it will be the name of the entry in the **Start** menu, and it will also be the name that shows in **Add or Remove Programs**.

 **Publisher name** will appear on the *publish.htm* page above **Product name**, and for an installed offline application, it will also be the name of the folder that contains the application's icon in the **Start** menu.

 The Start menu shortcut or app reference gets created in *%appdata%\Microsoft\Windows\Start Menu\Programs\\<publisher name\>*. The shortcut or app reference has the same name as the product name.

 You can set the **Product name** and **Publisher name** properties in the **Publish Options** dialog box, available on the **Publish** page of the **Project Designer**.

### To specify a Start menu name

1. With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.

2. Click the **Publish** tab.

   [!INCLUDE[ndptecclick](../deployment/includes/dotnet-publish-tool.md)]

3. Click the **Options** button to open the **Publish Options** dialog box.

4. Click **Description**.

5. In the **Publish Options** dialog box, enter the name to display in **Product name**.

6. Optionally, you can enter a publisher name in **Publisher name**.

## Related content
- [Publish ClickOnce applications](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)