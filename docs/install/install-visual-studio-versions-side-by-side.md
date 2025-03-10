---
title: Install Visual Studio versions side-by-side
description: Learn how to install Visual Studio on a computer that has an earlier or later version of Visual Studio already installed.
ms.custom: vs-acquisition
ms.date: 6/6/2023
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: anandmeg
ms.author: meghaanand
manager: jmartens
---
# Install Visual Studio versions side-by-side

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

You can install Visual Studio on a computer that has an earlier or later [major version](/visualstudio/productinfo/release-rhythm#determining-your-product-edition-version-and-channel) of Visual Studio already installed.

::: moniker range="vs-2019"

Before you install versions side-by-side, review the following conditions:

* If you use Visual Studio 2019 to open a solution that was created in Visual Studio 2017, you can later open and modify the solution again in the earlier version as long as you haven't implemented any features that are specific to Visual Studio 2019.

* If you try to use Visual Studio 2019 to open a solution that was created in Visual Studio 2017 or an earlier version, you might need to modify your projects and files to be compatible with Visual Studio 2019. For more information, see the [Port, migrate, and upgrade Visual Studio Projects](/visualstudio/releases/2019/port-migrate-and-upgrade-visual-studio-projects) page.

::: moniker-end

::: moniker range=">=vs-2022"

Before you install versions side-by-side, review the following conditions:

* If you use Visual Studio 2022 to open a solution that was created in Visual Studio 2017 or Visual Studio 2019, you can later open and modify the solution again in the earlier version as long as you haven't implemented any features that are specific to Visual Studio 2022.

* If you try to use Visual Studio 2022 to open a solution that was created in Visual Studio 2019 or an earlier version, you might need to modify your projects and files to be compatible with Visual Studio 2022. For more information, see the [Port, migrate, and upgrade Visual Studio Projects](/visualstudio/releases/2022/port-migrate-and-upgrade-visual-studio-projects) page.

::: moniker-end

* If you uninstall a version of Visual Studio on a computer that has more than one version installed, the file associations for Visual Studio are removed for all versions.

* Visual Studio doesn't automatically upgrade extensions because not all extensions are compatible. You must reinstall the extensions from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) or the software publisher.

## Install different editions of the same major Visual Studio version side-by-side

::: moniker range="vs-2019"

Each installation of Visual Studio must have a unique combination of major version, edition, and [update channel](/visualstudio/install/update-visual-studio?view=vs-2019&preserve-view=true#configure-source-location-of-updates). So, for example (if you had a machine with a lot of disk space), you can install Visual Studio 2019 Enterprise Preview ([preview channel](/visualstudio/productinfo/release-rhythm)) alongside Visual Studio 2019 Enterprise (release channel) alongside Visual Studio 2017 Professional (release channel) alongside Visual Studio 2017 Professional (custom layout channel).

When upgrading from one minor version of Visual Studio to the next, the Visual Studio installer will, by default, update your current installation to the latest version in that channel. For example, if version 16.11.24 was just released by Microsoft to the [Visual Studio 2019 release channel](/visualstudio/productinfo/release-rhythm), then the installer will try to replace your current installation of Visual Studio 2019 from the release channel with this latest version on the same channel. 

### Manual installation

You can manually use another bootstrapper to install a new instance of Visual Studio, or you can select one of the options from the Visual Studio Installer's **Available** tab.  

1. To use another bootstrapper, you can download and run one of the Visual Studio 2019 bootstrapper files from the [Visual Studio 2019 releases](/visualstudio/releases/2019/history#installing-an-earlier-release) page for the edition that you would like to install side-by-side with your existing installation of Visual Studio. If you are in an organization, your IT Administrator may have created a layout and provided a link to the bootstrapper in that layout.

::: moniker-end

::: moniker range=">=vs-2022"

Each installation of Visual Studio must have a unique combination of major version, edition, and [update channel](/visualstudio/install/update-visual-studio?view=vs-2022&preserve-view=true#configure-source-location-of-updates-1). So, for example (if you had a machine with a lot of disk space), you can install Visual Studio 2022 Enterprise Preview ([preview channel](/visualstudio/productinfo/release-rhythm)) alongside Visual Studio 2022 Enterprise (release channel) alongside Visual Studio 2019 Professional (release channel) alongside Visual Studio 2019 Professional (custom layout channel).

When upgrading from one minor version of Visual Studio to the next, the Visual Studio Installer will, by default, update your current installation to the latest version in that channel. For example, if version 17.3.9 was just released by Microsoft to the [Visual Studio 2022 release channel](/visualstudio/productinfo/release-rhythm), then the installer will try to replace your current installation of Visual Studio 2022 from the release channel with this latest version on the same channel. 

### Manual installation

You can manually use another bootstrapper to install a new instance of Visual Studio, or you can select one of the options from the Visual Studio Installer's **Available** tab.  

1. To use another bootstrapper, you can download and run one of the Visual Studio 2022 bootstrapper files from either the [Visual Studio downloads page](https://visualstudio.microsoft.com/downloads/?cid=learn-onpage-download-cta) or the [Visual Studio 2022 releases](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) page for the minor version that you would like to install side-by-side with your existing version of Visual Studio.

::: moniker-end

2. Using the installer's **Available** tab presumes, of course, that you already have some other version of Visual Studio installed. First find the **Visual Studio Installer** on your computer and launch it. After it updates itself, click on the **Available** tab and install one of the offered products. 

    :::image type="content" source="media/available-tab.png" alt-text="Screenshot showing the Visual Studio Installer's Available tab.":::


Then follow the steps to select the components you need for your installation. For more information, see [Install Visual Studio](install-visual-studio.md#step-4---choose-workloads).

> [!TIP]
> IT Administrators who want to suppress visibility of the Visual Studio Installer's **Available** tab or otherwise customize the availability of layout offerings on the **Available** tab can configure client registry and policies. Refer to [configure policies for enterprise deployments of Visual Studio](/visualstudio/install/configure-policies-for-enterprise-deployments) for more information. 
     
### Programmatic installation

You can also programmatically use either a bootstrapper or the installer to initiate a new installation of Visual Studio. Open a command prompt as administrator and run one of the following commands. Remember to specify a new folder path for the installation location and replace the .exe file name with the appropriate bootstrapper name for the edition of Visual Studio you are installing. 

To install via the bootstrapper:

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

To install using the installer that is already present on the client machine:

   ```shell
 "C:\Program Files (x86)\Microsoft Visual Studio\Installer\setup.exe" --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

Note that you can't initiate the installer programmatically from the same directory that the installer resides in.

## .NET Framework versions and side-by-side installations

Visual Basic, Visual C#, and Visual F# projects use the **Target Framework** option in the **Project Designer** to specify the version of the .NET Framework that'll be used. For a C++ project, you can manually change the target framework by modifying the .vcxproj file. For more information, see the [Version compatibility in the .NET Framework](/dotnet/framework/migration-guide/version-compatibility) page.

When you create a project, you can specify which version of the .NET Framework the project targets in the **.NET Framework** list in the **New Project** dialog box.

For language-specific information, see the appropriate topic in the following table.

::: moniker range=">= vs-2019"

| Language     | Topic                                                                                                                           |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)         |
| Visual C#    | [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)                         |
| Visual F#    | [Develop with Visual F# in Visual Studio](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [How to: Modify the target framework and platform toolset](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## Related content

* [Install Visual Studio](install-visual-studio.md)
* [Port, migrate, and upgrade Visual Studio projects](/visualstudio/releases/2022/port-migrate-and-upgrade-visual-studio-projects)
* [Building C/C++ isolated applications and side-by-side assemblies](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
