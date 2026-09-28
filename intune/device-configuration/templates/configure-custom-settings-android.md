---
layout: Conceptual
title: Add custom settings to Android DA devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-android
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
description: Add or create a custom profile for Android device administrator (DA) devices in Microsoft Intune. Create a WiFi profile with a preshared key, create a per-app VPN profile, or allow/block apps for Samsung Knox Standard devices.
ms.date: 2025-02-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: anuragjain
locale: en-us
document_id: ddc8be09-5eed-5077-b777-28b8ee14cd3e
document_version_independent_id: ddc8be09-5eed-5077-b777-28b8ee14cd3e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-custom-settings-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-custom-settings-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-custom-settings-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 55b44a9a-714b-8b39-f39c-51dc123c8424
---

# Add custom settings to Android DA devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Using Microsoft Intune, you can add or create custom settings for your Android devices using a **custom profile**. Custom profiles are a feature in Intune. They're designed to add device settings and features that aren't built in to Intune.

This feature applies to:

- Android device administrator (DA)

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Android custom profiles use Open Mobile Alliance Uniform Resource Identifier (OMA-URI) settings to configure different features on Android devices. These settings are typically used by mobile device manufacturers to control these features.

Using a custom profile, you can configure and assign the following Android settings. The following settings aren't built in to Intune:

- [Create a Wi-Fi profile with a pre-shared key](create-wifi-preshared-key)
- [Create a per-app VPN profile](configure-per-app-vpn-android)
- [Allow and block apps for Samsung Knox Standard devices](manage-apps-samsung-knox)
- [Configure web protection in Microsoft Defender for Endpoint for Android](../../device-security/microsoft-defender/configure-web-protection-android)

Important

Only the settings listed can be configured in a custom profile. Android devices don't expose a complete list of OMA-URI settings you can configure.

This article shows you how to create a custom profile for Android DA devices.

## Prerequisites

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following settings:

    - **Platform**: Select **Android device administrator**.
    - **Profile type**: Select **Custom**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Android DA custom profile**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings** &gt; **OMA-URI Settings**, select **Add**. Enter the following settings:

    - **Name**: Enter a unique name for the OMA-URI setting so you can easily find it.
    - **Description**: Enter a description that gives an overview of the setting, and any other important details.
    - **OMA-URI**: Enter the OMA-URI you want to use as a setting.
    - **Data type**: Select the data type for this OMA-URI setting. Your options:

        - String
        - String (XML file)
        - Date and time
        - Integer
        - Floating point
        - Boolean
        - Base64 (file)
    - **Value**: Enter the data value you want to associate with the OMA-URI you entered. The value depends on the data type you selected. For example, if you select **Date and time**, select the value from a date picker.
8. Select **Save** to save your changes. Continue to add more settings as needed. After you add some settings, you can select **Export**. **Export** creates a list of all the values you added in a comma-separated values (.csv) file.

    Select **Next**.
9. In **Scope tags** (optional) &gt; **Select scope tags**, choose your scope tags to assign to the profile. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the groups that will receive this profile. For more information on assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, when you're done, choose **Create**. The profile is created, and shown in the list.

    You can also [monitor its status](../monitor-device-profile).