---
layout: Conceptual
title: Custom per-app VPN profile for Android DA in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-per-app-vpn-android
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
description: Use a custom profile for per-app VPN profiles on Android device administrator with the Pulse Secure or Citrix VPN connection types in Microsoft Intune.
ms.date: 2026-05-06T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: abalwan
locale: en-us
document_id: a0307ccc-af9f-cb4d-2bd4-a6bc94091c0e
document_version_independent_id: a0307ccc-af9f-cb4d-2bd4-a6bc94091c0e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-per-app-vpn-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-per-app-vpn-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-per-app-vpn-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
platformId: 6b33412e-8462-343b-f301-4c13278c1ad3
---

# Custom per-app VPN profile for Android DA in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

You can create a per-app VPN profile for Android 8.0 and later devices that are enrolled in Intune. First, create a VPN profile that uses either the Pulse Secure or Citrix connection type. Then, create a custom configuration policy that associates the VPN profile with specific apps.

This feature applies to:

- Android device administrator (DA) enrolled in Intune

To use per-app VPN on Android Enterprise devices, use an [app configuration policy](../../app-management/configuration/configure-vpn-android). App configuration policies support more VPN client apps. On Android Enterprise devices, you can use the steps in this article. But, it's not recommended, and you're limited to only Pulse Secure and Citrix VPN connections.

After you assign the policy to your Android DA device or user groups, users should start the Pulse Secure or Citrix VPN client. Then, the VPN client allows only traffic from the specified apps to use the open VPN connection.

Note

Only the Pulse Secure and Citrix connection types are supported for Android device administrator. On Android Enterprise devices, use an [app configuration policy](../../app-management/configuration/configure-vpn-android).

## Prerequisites

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
- The device must be enrolled and MDM managed by Intune. For information on the enrollment options for Android devices, go to [Android enrollment guide for Microsoft Intune](../../device-enrollment/android/guide).

## Step 1 - Create a VPN profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Android device administrator**.
    - **Profile type**: Select **VPN**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Android DA per-app VPN profile for entire company**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, configure the settings you want in the profile:

    - [VPN settings for Android device administrator devices](ref-vpn-settings-android).

    Take note of the **Connection Name** value you enter when creating the VPN profile. This name is needed in the next step. In this example, the connection name is **MyAppVpnProfile**.
8. Select **Next**, and continue creating your profile. For more information, go to [Create a VPN profile](configure-vpn#step-2---create-the-profile).

## Step 2 - Create a custom configuration policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Android device administrator**.
    - **Profile type**: Select **Custom**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the custom profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Android DA - OMA-URI VPN**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings** &gt; **OMA-URI Settings**, select **Add**. Enter the following OMA-URI values:

    - **Name**: Enter a name for your setting.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **OMA-URI**: Enter `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, where *Name* is the connection name you noted in Step 1. In this example, the string is `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Data type**: Enter **String**.
    - **Value**: Enter a semicolon-separated list of packages to associate with the profile. For example, if you want Excel and the Google Chrome browser to use the VPN connection, enter `com.microsoft.office.excel;com.android.chrome`.

    Your settings look similar to the following settings:

    ![Screenshot that shows Android device administrator per-app VPN custom policy in Microsoft Intune.](media/configure-per-app-vpn-android/android_per_app_vpn_oma_uri.png)
8. Select **Next**, and continue creating your profile. For more information, go to [Create a VPN profile](configure-vpn#step-2---create-the-profile).

### Set your blocked and allowed app list (optional)

Use the following steps to enter the list apps that are allowed or blocked from using the VPN connection:

1. On the **Custom OMA-URI Settings** pane, choose **Add**.
2. Enter a setting name.
3. In **OMA-URI**, enter `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, where *Name* is the VPN profile name you noted in Step 1. In our example, the string is `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. In **Data type**, enter **String**.
5. In **Value**, enter one of the following Android values:

    - `BLACKLIST`: Enter a list of apps that can't use the VPN connection. All other apps connect through the VPN.
    - `WHITELIST`: Enter a list of apps that can use the VPN connection. Apps that aren't on the list don't connect through the VPN.

## Step 3 - Assign both policies

[Assign both device profiles](../assign-device-profile) to the required users or devices.

## Resources

- For a list of all the Android device administrator VPN settings, go to [Android device settings to configure VPN](ref-vpn-settings-android).
- To learn more about VPN settings and Intune, go to [configure VPN settings in Microsoft Intune](configure-vpn).