---
title: XSLT Default Templates
description: Learn about the XSLT default templates that are used during XSLT processing when there is no matching explicit template rule in the style sheet.
ms.date: 11/04/2016
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
manager: jmartens
ms.technology: vs-xml-tools
---
# XSLT default templates

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

A default template is used during XSLT processing when there is no matching explicit template rule in the style sheet. The default template, also referred to as built-in template rule, is defined in section 5.8 of the W3C XSLT 1.0 Recommendation. The default template allows the XSLT processor to process a node, even though there is no explicit template rule that matches it. However, because the built-in template rule is not explicitly defined in the style sheet, this may lead to unexpected or confusing XSLT transformation results.

The XSLT debugger now displays the code of XSLT default templates. When you step through an XSLT transformation, if a default template is used, the debugger displays the default template in a window. This enables you to step through the code of the default template and set breakpoints on its instructions.

## Related content

- [Debugging XSLT](../xml-tools/debugging-xslt.md)
