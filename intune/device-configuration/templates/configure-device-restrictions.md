---
layout: Conceptual
title: Restrict devices features using policy in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-restrictions
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
description: Add a device configuration profile to restrict features on Android device administrator, Android Enterprise, AOSP, macOS, iOS, iPadOS, and Windows 10/11 client devices in Microsoft Intune.
ms.date: 2025-10-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: befeca58-7c49-0917-5a08-7bb3359166e6
document_version_independent_id: befeca58-7c49-0917-5a08-7bb3359166e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-device-restrictions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-device-restrictions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-device-restrictions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 611dfadb-02bc-6471-e36c-f443cb337a12
---

# Restrict devices features using policy in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Intune includes device restriction policies that help administrators control Android, iOS/iPadOS, macOS, and Windows devices. These restrictions let you control a wide range of settings and features to protect your organization's resources. For example, admins can:

- Allow or block the device camera.
- Control access to Google Play, app stores, viewing documents, and gaming.
- Block built-in apps, or create a list of apps that allowed or prohibited.
- Allow or prevent backing up files to cloud and storage accounts.
- Set a minimum password length, and block simple passwords.

These features are available in Intune, and are configurable by the administrator. Intune uses **configuration profiles** to create and customize these settings for your organization's needs. After you add these features in a profile, you then assign the profile to devices in your organization.

This feature applies to:

- Android device administrator
- Android Open Source Project (AOSP)
- Android Enterprise personally owned devices with a work profile
- iOS/iPadOS
- macOS
- Windows

This article shows you how to create a device restrictions profile. You can also see all the available settings for the different platforms.

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select the platform of your devices. Your options:

        - **Android device administrator**
        - **Android (AOSP)**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows 10 and later**
    - **Profile type**: Select **Device restrictions**. Or, select **Templates** &gt; **Device restrictions**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **iOS/iPadOS: Block camera on devices**.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Select your platform for detailed settings:

    - [Android](ref-device-restrictions-android-enterprise)
    - [iOS/iPadOS](ref-device-restrictions-apple)
    - [macOS](ref-device-restrictions-apple)
    - [Windows](ref-device-restrictions-windows)
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, like `US-NC IT Team` or `JohnGlenn_ITDepartment`. For information about scope tags, go to [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the users or groups that will receive your profile. For information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.