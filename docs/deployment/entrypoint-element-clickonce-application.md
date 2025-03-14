---
title: "&lt;entryPoint&gt; Element (ClickOnce Application)"
description: The entryPoint element identifies the assembly that should be executed when this ClickOnce application is run on a client computer.
ms.date: "11/04/2016"
ms.topic: "reference"
f1_keywords:
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs:
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords:
  - "<entryPoint> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], entryPoint element"
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
---
# &lt;entryPoint&gt; element (ClickOnce application)

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
Identifies the assembly that should be executed when this ClickOnce application is run on a client computer.

## Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## Elements and attributes
 The `entryPoint` element is required and is in the `urn:schemas-microsoft-com:asm.v2` namespace. There may only be one `entryPoint` element defined in an application manifest.

 The `entryPoint` element has the following attribute.

|Attribute|Description|
|---------------|-----------------|
|`name`|Optional. This value is not used by .NET Framework.|

 `entryPoint` has the following elements.

## assemblyIdentity
 Required. The role of `assemblyIdentity` and its attributes is defined in [\<assemblyIdentity> Element](../deployment/assemblyidentity-element-clickonce-application.md).

 The `processorArchitecture` attribute of this element and the `processorArchitecture` attribute defined in the `assemblyIdentity` elsewhere in the application manifest must match.

## commandLine
 Required. Must be a child of the `entryPoint` element. It has no child elements and has the following attributes.

| Attribute | Description |
|--------------| - |
| `file` | Required. A local reference to the startup assembly for the ClickOnce application. This value cannot contain forward slash (/) or backslash (\\) path separators. |
| `parameters` | Required. Describes the action to take with the entry point. The only valid value is `run`; if a blank string is supplied, `run` is assumed. |

## customHostRequired
 Optional. If included, specifies that this deployment contains a component that will be deployed inside of a custom host, and is not a stand-alone application.

 If this element is present, the `assemblyIdentity` and `commandLine` elements must not also be present. If they are, ClickOnce will raise a validation error during installation.

 This element has no attributes and no children.

## customUX
 Optional. Specifies that the application is installed and maintained by a custom installer, and does not create a Start menu entry, shortcut, or Add or Remove Programs entry.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 An application that includes the customUX element must provide a custom installer that uses the <xref:System.Deployment.Application.InPlaceHostingManager> class to perform install operations. An application with this element cannot be installed by double-clicking its manifest or setup.exe prerequisite bootstrapper. The custom installer can create Start menu entries, shortcuts, and Add or Remove Programs entries. If the custom installer does not create an Add or Remove Programs entry, it must store the subscription identifier provided by the <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> property and enable the user to uninstall the application later by calling the <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> method. For more information, see [Walkthrough: Creating a Custom Installer for a ClickOnce Application](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## Remarks
 This element identifies the assembly and entry point for the ClickOnce application.

 You cannot use `commandLine` to pass parameters into your application at run time. You can access query string parameters for a ClickOnce deployment from the application's <xref:System.AppDomain>. For more information, see [How to: Retrieve Query String Information in an Online ClickOnce Application](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## Example
 The following code example illustrates an `entryPoint` element in an application manifest for a ClickOnce application. This code example is part of a larger example provided for the [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md) topic.

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## See also
- [ClickOnce application manifest](../deployment/clickonce-application-manifest.md)
