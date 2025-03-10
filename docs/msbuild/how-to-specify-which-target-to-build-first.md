---
title: 'Specify Which Target to Build First'
description: Specify the initial targets (InitialTargets) or the default targets (DefaultTargets) to build first in MSBuild project files.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
---
# Specify which target to build first

A project file can contain one or more `Target` elements that define how the project is built. The Microsoft Build Engine (MSBuild) engine builds the first target it finds, and any dependencies, unless the project file contains a `DefaultTargets` attribute, an `InitialTargets` attribute, or a target is specified at the command line using the **-target** switch.
## Use the InitialTargets attribute

The `InitialTargets` attribute of the `Project` element specifies a target that will run first, even if targets are specified on the command line or in the `DefaultTargets` attribute.

#### To specify one initial target

- Specify the default target in the `InitialTargets` attribute of the `Project` element. For example:

   `<Project InitialTargets="Clean">`

  You can specify more than one initial target in the `InitialTargets` attribute by listing the targets in order, and using a semicolon to separate each target. The targets in the list will be run sequentially.

#### To specify more than one initial target

- List the initial targets, separated by semicolons, in the `InitialTargets` attribute of the `Project` element. For example, to run the `Clean` target and then the `Compile` target, type:

     `<Project InitialTargets="Clean;Compile">`

## Use the DefaultTargets attribute

 The `DefaultTargets` attribute of the `Project` element specifies which target or targets are built if a target is not specified explicitly on the command line. If targets are specified in both the `InitialTargets` and `DefaultTargets` attributes and no target is specified on the command line, MSBuild runs the targets specified in the `InitialTargets` attribute followed by the targets specified in the `DefaultTargets` attribute.

#### To specify one default target

- Specify the default target in the `DefaultTargets` attribute of the `Project` element. For example:

   `<Project DefaultTargets="Compile">`

  You can specify more than one default target in the `DefaultTargets` attribute by listing the targets in order, and using a semicolon to separate each target. The targets in the list will be run sequentially.

#### To specify more than one default target

- List the default targets, separated by semicolons, in the `DefaultTargets` attribute of the `Project` element. For example, to run the `Clean` target and then the `Compile` target, type:

     `<Project DefaultTargets="Clean;Compile">`

## Use the -target Switch

 If a default target is not defined in the project file, or if you do not want to use that default target, you can use the command line switch **-target** to specify a different target. The target or targets specified with the **-target** switch are run instead of the targets specified by the `DefaultTargets` attribute. Targets specified in the `InitialTargets` attribute always run first.

#### To use a target other than the default target first

- Specify the target as the first target using the **-target** command line switch. For example:

     `msbuild file.proj -target:Clean`

#### To use several targets other than the default targets first

- List the targets, separated by semicolons or commas, using the **-target** command line switch. For example:

     `msbuild <file name>.proj -t:Clean;Compile`

## Related content

- [MSBuild](../msbuild/msbuild.md)
- [Targets](../msbuild/msbuild-targets.md)
- [How to: Clean a build](../msbuild/how-to-clean-a-build.md)
