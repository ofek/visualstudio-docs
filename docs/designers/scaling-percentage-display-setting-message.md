---
title: Scaling on your main display is set to X%
description: Learn about the scaling percentage settings message you see with Windows Forms Designer on HDPI monitors, and what to do next.
ms.date: 06/29/2023
ms.topic: ui-reference
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-ide-designers
ms.custom: engagement-fy23
---
# Scaling on your main display is set to X%

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

When you open a form in **Windows Forms Designer** on an HDPI monitor, Visual Studio displays an information bar with a message that includes the monitor's current scaling percentage and an option to restart Visual Studio at 100% scaling. Restarting at 100% scaling allows for proper rendering without overlap.

:::image type="content" source="media/scaling-gold-bar-message-1.png" alt-text="Screenshot of the information bar in Visual Studio to restart in DPI-unaware mode.":::

## Why this message appears and what to do about it

Here's why the message appears:

- Windows Forms Designer is [DPI-unaware](disable-dpi-awareness.md#windows-forms-designer-is-dpi-unaware), while Visual Studio is DPI-aware. 
- To accurately display Forms elements in the Designer, you can set Visual Studio to 100% scaling so that it, too, is DPI-unaware. 
- When Visual Studio is set to 100% scaling, fonts might appear blurry and you might see issues in other designers, such as the XAML Designer, which are DPI-aware. 

Here's what to do about it:

- Select the **Restart Visual Studio with 100% scaling** link in the message on the information bar to [restart Visual Studio as a DPI-unaware process](disable-dpi-awareness.md#restart-visual-studio-as-a-dpi-unaware-process), which means that it restarts at 100% scaling (96 DPI).
- You can also [set the scaling size in Windows](disable-dpi-awareness.md#use-windows-to-set-your-display-scaling-to-100) to 100%, but it can make the user interface (UI) too small to be usable.
- When Visual Studio runs as DPI-unaware, the designer layout issues are resolved. However, fonts might appear blurry and issues can appear in other designers such as the XAML Designer. 
- If you've previously set Visual Studio to 100% scaling and want to re-enable DPI awareness, select the **Restart Visual Studio with automatic scaling** link in the information bar to restart Visual Studio as DPI-aware. 

## Next steps

For more information about HDPI scaling issues and detailed, step-by-step instructions on how to fix them, see [HDPI/scaling issues with Windows Forms Designer in Visual Studio](disable-dpi-awareness.md).