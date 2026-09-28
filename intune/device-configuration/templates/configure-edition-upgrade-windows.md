---
layout: Conceptual
title: Upgrade Windows editions or switch S mode using Intune policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-edition-upgrade-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use Microsoft Intune to upgrade Windows 10/11 client devices to a different edition, or switch S mode. Administrators can use a device configuration profile to upgrade Windows client Professional to Windows client Enterprise, and switch out of S mode. See the supported upgrade paths for Windows 10/11 Pro, N Edition, Education, Cloud, Enterprise, Core, and Holographic.
ms.date: 2024-04-22T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: 061c0c4e-2618-a4d6-8fd0-69e652e54050
document_version_independent_id: 061c0c4e-2618-a4d6-8fd0-69e652e54050
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-edition-upgrade-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-edition-upgrade-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-edition-upgrade-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: aede8a35-4b50-9612-9c1c-96363b381e7d
---

# Upgrade Windows editions or switch S mode using Intune policy - Microsoft Intune | Microsoft Learn

You can create a Microsoft Intune policy that upgrades Windows editions, or switches out of S mode.

As part of your mobile device management (MDM) solution, you can upgrade your Windows devices. For example, you want to upgrade your Windows Professional devices to Windows Enterprise. Or, you want the Windows device to switch out of S mode.

[Windows S mode](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) (opens another Microsoft web site) is designed for security and performance. You can use Intune to switch out of S mode. Switching out of S mode is one way. So once you switch out of S mode, you can't go back to Windows S mode.

For more information, go to [commonly asked questions about S mode](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq).

This feature applies to:

- Windows
- Windows Holographic for Business

Intune uses **configuration profiles** to create and customize these settings for your organization's needs. After you add these features in a profile, you can then push or deploy the profile to Windows client devices in your organization. When you deploy the profile, Intune automatically upgrades the devices or switches out of S mode. When the device checks-in with the Intune service, the policy applies and Intune upgrades the device or switches out of S mode.

This article lists the supported upgrade paths, and shows you how to create the device configuration profile. For a list of all the available upgrade and S mode settings you can configure, go to [Windows client device settings to upgrade editions or enable S mode in Intune](ref-edition-upgrade-settings-windows).

Note

If you remove the policy assignment later, the version of Windows on the device isn't reverted. The device continues to run normally.

## Prerequisites

- To install the updated Windows version on the devices that you target with the policy (for Windows client Desktop editions), you need a valid product key. You can use either Multiple Activation Keys (MAK) or Key Management Server (KMS) keys.
- For Windows Holographic editions, you can use a Microsoft license file. The license file includes the licensing information to install the updated edition on all devices that you target with the policy.
- The Windows client devices you assign the policy are enrolled in Microsoft Intune.
- To create the policy, at a minimum, sign in with an account that has the **Policy and Profile Manager** Intune role. For more information, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Supported upgrade paths

The following table lists the supported upgrade paths for the Windows edition upgrade profile.

| Upgrade from | Upgrade to |
| --- | --- |
| Windows Pro | Windows Education Windows Enterprise Windows Pro Education |
| Windows Pro N edition | Windows Education N edition Windows Enterprise N edition Windows Pro Education N edition |
| Windows Pro Education | Windows Education |
| Windows Pro Education N edition | Windows Education N edition |
| Windows Cloud | Windows Education Windows Enterprise Windows Pro Windows Pro Education |
| Windows Cloud N edition | Windows Education N edition Windows Enterprise N edition Windows Pro N edition Windows Pro Education N edition |
| Windows Enterprise | Windows Education |
| Windows Enterprise N edition | Windows Education N edition |
| Windows Core | Windows Education Windows Enterprise Windows Pro Education |
| Windows Core N edition | Windows Education N edition Windows Enterprise N edition Windows Pro Education N edition |

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Edition upgrade and mode switch**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile. For example, enter something like `Windows edition upgrade profile` or `Windows - turn off S mode`.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, enter the settings you want to configure. For a list of all settings, and what they do, go to:

    - [Windows upgrade and S mode](ref-edition-upgrade-settings-windows)
    - [Windows Holographic for Business](ref-holographic-upgrade-settings)
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the users or user group that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in with Intune, the policy applies.