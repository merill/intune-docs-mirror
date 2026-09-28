---
layout: Conceptual
title: Use custom device settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings
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
description: Add or create a profile to use custom settings for Windows 10/11 client, Android device administrator, Android Enterprise, macOS, and iOS/iPadOS devices using Microsoft Intune.
ms.date: 2026-02-05T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: 095999e0-014c-cf8c-474f-b80b503aef40
document_version_independent_id: 095999e0-014c-cf8c-474f-b80b503aef40
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-custom-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-custom-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-custom-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c427024-e6db-0ec7-84e5-3fa72368b2f1
---

# Use custom device settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune includes many built-in settings to control different features on a device. If there are device settings and features that aren't built in to Intune, then you can create custom profiles. Custom profiles are created similar to built-in profiles.

This feature applies to:

- Android device administrator
- iOS/iPadOS
- macOS
- Windows

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Custom settings are configured differently for each platform. For example, to control features on Android and Windows devices, you enter Open Mobile Alliance Uniform Resource Identifier (OMA-URI) values. For Apple devices, you import a file you created with the [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) or [Apple Profile Manager](https://support.apple.com/profile-manager).

For an overview of device configuration profiles, go to [What are Microsoft Intune device profiles?](../overview).

This article shows you how to create a custom device configuration profile in Intune. You can also see all the available settings for the different platforms.

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Choose the platform of your devices. Your options:

        - **Android device administrator**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows 10 and later**
    - **Profile type**: Select **Custom**. Or, select **Templates** &gt; **Custom**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Windows: AllowVPNOverCellular custom OMA-URI**.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Choose your platform for detailed settings:

    - [Android device administrator](configure-custom-settings-android)
    - [iOS/iPadOS or macOS](configure-custom-settings-apple)
    - [Windows](configure-custom-settings-windows)
    - [Windows Holographic for Business](ref-custom-settings-windows-holographic)
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the users or groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

## Example

In the following example, the **Connectivity/AllowVPNOverCellular** setting is enabled. This setting allows a Windows client device to open a VPN connection when on a cellular network.

![Screenshot that shows an example of a custom policy containing VPN settings in Microsoft Intune.](media/configure-custom-settings/custom-policy-example.png)