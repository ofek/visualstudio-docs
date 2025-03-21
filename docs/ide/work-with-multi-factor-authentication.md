---
title: Multi-factor authentication with Visual Studio sign-ins
titleSuffix: "" 
ms.date: 08/24/2023
ms.topic: how-to
description: Use Visual Studio with accounts that require multifactor authentication (MFA) to protect your apps and data with conditional access policies.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
---

# Sign in to Visual Studio with accounts that require multi-factor authentication (MFA)

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

In this article, you'll learn how to use Visual Studio with accounts that require multi-factor authentication (MFA).

## Why enable MFA policies?

When collaborating with external guest users, it's a good idea to protect your apps and data with **conditional access (CA)** policies such as **multi-factor authentication (MFA)**.  

Once enabled, guest users will need more than just a username and password to access your resources, and must satisfy additional security requirements. MFA policies can be enforced at the tenant, app, or individual guest user level, the same way that they are enabled for members of your own organization. 

## How is the Visual Studio experience affected by MFA policies?
Versions of Visual Studio prior to 16.6 may have degraded authentication experiences when used with accounts that have enabled CA policies such as MFA, and are associated with two or more tenants.

These issues can cause your instance of Visual Studio to prompt reauthentication multiple times per day. You may have to re-enter your credentials for previously authenticated tenants, even during the course of the same Visual Studio session.

## Using Visual Studio with MFA policies

::: moniker range="<=vs-2019"

You can access resources secured via CA policies such as MFA in Visual Studio. To use this enhanced workflow, you'll need to opt into using your system's default web browser as the mechanism to add and reauthenticate Visual Studio accounts. 

::: moniker-end

::: moniker range="=vs-2022"

You can access resources secured via CA policies such as MFA in Visual Studio. To use this enhanced workflow, you'll need to opt into using your system's default web browser or the Windows authentication broker (available in [Visual Studio version 17.5](/visualstudio/releases/2022/release-notes-v17.5), but we recommend using [Visual Studio version 17.7](/visualstudio/releases/2022/release-notes) for an optimal experience) as the mechanism to add and reauthenticate Visual Studio accounts. 

::: moniker-end

> [!WARNING]
> Not using this workflow could trigger a degraded experience resulting in multiple additional authentication prompts when adding or reauthenticating Visual Studio accounts. 

::: moniker range="=vs-2022"

### Enabling Windows authentication broker

>[!NOTE]
>Web Account Manager(WAM) is only available on Windows 10 and above, as well as Windows Server 2019 and above.

To enable this workflow, go to Visual Studio's Options dialog **(Tools > Options…)**, select the **Accounts** tab, and then select **Windows authentication broker** from the **Add and reauthenticate accounts using:** dropdown. 

:::image type="content" source="media/vs-2022/windows-authentication-broker.png" alt-text="Select web authentication broker from the dropdown.":::

Windows authentication broker uses [Web Account Manager(WAM)](/entra/msal/dotnet/acquiring-tokens/desktop-mobile/wam) and offers many benefits such as security, improved MFA support, and seamless integration between accounts added to the OS and Visual Studio.

::: moniker-end

### Enabling system web browser

> [!NOTE] 
> For the best experience, we recommend that you clear your system’s default web browser data before proceeding with this workflow. Additionally, if you have Work or School accounts in your Windows 10 Settings under **Access work or school**, please verify that they are properly authenticated.

To enable this workflow, go to Visual Studio's Options dialog **(Tools > Options…)**, select the **Accounts** tab and select **System web browser** from the **Add and reauthenticate accounts using:** dropdown. 

:::image type="content" source="media/vs-2022/select-system-web-browser.png" alt-text="Select system web browser from the menu.":::

### Sign into additional accounts with MFA policies 

::: moniker range="=vs-2022"

**Windows authentication broker**

Once the Windows authentication broker workflow is enabled, you can sign in or add accounts to Visual Studio as you normally would, via the Account Settings dialog **(File > Account Settings…)**. Web Account Manager(WAM) simplifies the sign in experience by allowing users to log in with accounts known to Windows, such as the account signed into your Windows session.

:::image type="content" source="media/vs-2022/add-personalization-account-web-account-manager.png" alt-text="Add additional accounts to Visual Studio with the Windows authentication broker workflow.":::

**System web browser**

::: moniker-end

Once the system web browser workflow is enabled, you can sign in or add accounts to Visual Studio as you normally would, via the Account Settings dialog **(File > Account Settings…)**.   
</br>
:::image type="content" source="media/vs-2022/add-personalization-account.png" alt-text="Add a new personalization account to Visual Studio." border="false":::

This action will open your system's default web browser, ask you to sign into your account, and validate any required MFA policy.

During the sign-in process, you may receive an additional prompt asking you to stay signed in. This prompt will likely show up the second time an account is used to sign in. To minimize the need to re-enter your credentials, we recommend that you select **Yes**, as this ensures your credentials are preserved across browser sessions.

:::image type="content" source="media/vs-2022/keep-me-signed-in.png" alt-text="Stay signed in?":::

Based on your development activities and resource configuration, you may still be prompted to re-enter your credentials during your session. This can occur when you add a new resource, or try accessing a resource without having previously met its CA/MFA authorization requirements.

## Reauthenticating an account

If there's a problem with your account, Visual Studio might ask you to re-enter your account credentials.  

:::image type="content" source="media/vs-2022/reauthenticate-account.png" alt-text="Screenshot showing account that needs reauthentication.":::

Clicking on **Re-enter your credentials** will open your system's default web browser and attempt to automatically refresh your credentials. If unsuccessful, you'll be asked to sign into your account and validate any required CA/MFA policy.

If your account is associated with multiple Azure Active Directories and runs into an access problem with one or more of them, the **Re-enter your credentials** dialog will show you the impacted directories and the associated [AADSTS error codes](/azure/active-directory/develop/reference-error-codes#aadsts-error-codes). 

You'll be able de-select any directories that you don't want to reauthenticate and **continue** a regular signing in operation with the home directory, as well as any guest tenants that remain selected. Deselected directories won't be accessible for future use until the [account filter](work-with-multi-factor-authentication.md#how-to-filter-out-individual-tenants) is removed.

:::image type="content" source="media/vs-2022/reauthenticate-client-access-problem-directories.png" alt-text="Reauthenticate your Visual Studio account.":::

> [!NOTE] 
> For the best experience, keep your browser open until all CA/MFA policies are validated for your resources. Closing the browser may result in losing the previously built MFA state, and may prompt additional authorization prompts.

## Troubleshoot sign in issues

### CA/MFA issues

If you're experiencing CA/MFA issues and/or are unable to log in even when using the system web browser, try the following steps to resolve the issue:

1. [Sign out](signing-in-to-visual-studio.md#sign-out-of-account) of the account in Visual Studio.
1. Select **Tools** > **Options** > **Accounts** > Uncheck **Authenticate across all Azure Active Directories**.
1. Sign in again.

> [!NOTE]
> After these steps you'll likely be able to log in, but your account will be put in a filtered state. While in a filtered state, only your account's default tenant and resources will be available. All other Microsoft Entra tenants and resources will become inaccessible, but you can [manually add them back](#how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio).

### Pre-authorization issues

:::image type="content" source="media/vs-2022/pre-auth-general.png" alt-text="Screenshot of a pre-authorization error dialog." border="false":::

Starting with Visual Studio 2022 version 17.5, if you see the previous error dialog, try the following steps to resolve the issue:

1. [Sign out](signing-in-to-visual-studio.md#sign-out-of-account) of the account in Visual Studio.
1. Sign in again.
1. Create a new [Report a Problem](https://developercommunity.visualstudio.com/VisualStudio/report) ticket explaining the activity you were doing and/or resource you were trying to access before encountering the problem.

> [!NOTE]
> Creating a ticket will help us identify problematic areas and provide the needed logs to investigate and address the issue.

### Sign in issues with Government Clouds

:::image type="content" source="media/vs-2022/pre-auth-gov.png" alt-text="Screenshot of a sign-in error when trying to access government clouds." border="false":::

Starting with Visual Studio 2022 version 17.5, if you see the previous error dialog or experience issues during sign in operations, try the following steps to resolve the issue:

1. Close Visual Studio.
1. Open the "Developer Command Prompt" for your specific Visual Studio installation.
1. Enter ```Set DisableWAMClientIdForVS=true```. Alternatively, you can use ```Setx DisableWAMClientIdForVS true``` to set a user variable on your system. Once you've set up a user variable, you won't have to do this again.
1. After setting the user variable, open Visual Studio from the Developer Command Prompt: ```devenv```.
1. Sign in again.

<a name='how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio'></a>

## How to opt out of using a specific Microsoft Entra tenant in Visual Studio

Visual Studio 2019 version 16.6 and above offers the flexibility to filter out tenants individually or globally, effectively hiding them from Visual Studio. Filtering eliminates the need to authenticate with that tenant, but it also means that you won't be able to access any associated resources.

This functionality is useful when you have multiple tenants, but want to optimize your development environment by targeting a specific subset. It can also help in instances when you can't validate a particular CA/MFA policy, as you can filter out the offending tenant. 

### How to filter out all tenants
To globally filter out all tenants, open the Account Settings dialog **(File > Account Settings... > Account options)** and deselect the **Authenticate across all Azure Active Directories** checkbox.

Deselecting that option ensures you’ll only authenticate with the account’s default tenant. It also means that you won't be able to access any resources associated with other tenants your account might be a guest on.

### How to filter out individual tenants
To filter tenants that are associated with your Visual Studio account, open the Account Settings dialog **(File > Account Settings…)** and click on **Apply filter**. 
</br>
</br>

:::image type="content" source="media/vs-2022/apply-filter.png" alt-text="Apply filter." border="false":::

The **Filter account** dialog will appear, allowing you to select which tenants you want to use with your account. 

:::image type="content" source="media/vs-2022/select-filter-account.png" alt-text="Select account to filter.":::

After you deselect the tenant to filter, the **Account Settings** and the **Filter account** dialogs will show filtered state.

:::image type="content" source="media/vs-2022/account-settings-filter-account-dialogs-tenants-filtered-out-state.png" alt-text="Screenshot showing the filtered tenant state on the Account Settings and the Filter Account dialogs":::

## Related content

- [Sign in to Visual Studio](signing-in-to-visual-studio.md)
- [Sign in to Visual Studio for Mac](/visualstudio/mac/signing-in)
