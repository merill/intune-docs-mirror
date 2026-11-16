---
layout: Conceptual
title: Grant Android app permissions by using Android Enterprise OEMConfig - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-managed-home-screen-permissions-android
author: iceorbital
ms.author: acabello
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use Android Enterprise OEMConfig in Microsoft Intune to grant required permissions to Managed Home Screen and to the Intune app for Local Actions scenarios on supported Android devices.
ms.date: 2026-09-30T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: abigailstein
ms.custom: msecd-doc-authoring-1023
ai-usage: ai-assisted
locale: en-us
document_id: eeb420e1-dabf-737c-c24e-1686095d35d1
document_version_independent_id: eeb420e1-dabf-737c-c24e-1686095d35d1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-managed-home-screen-permissions-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-managed-home-screen-permissions-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-managed-home-screen-permissions-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 15706470-d344-4d95-8445-002d74413696
---

# Grant Android app permissions by using Android Enterprise OEMConfig - Microsoft Intune | Microsoft Learn

Use Android Enterprise OEMConfig in Microsoft Intune to grant app permissions on dedicated and fully managed devices without asking users to approve them manually. This approach helps you configure Managed Home Screen (MHS) and supports Intune app scenarios that need permission before the app can bring an experience to the foreground.

Before you begin, review the prerequisites later in this article. In this article, you add the OEMConfig app from Managed Google Play, create an OEMConfig profile, and configure the app entries that grant permissions to MHS or to the Intune app. For Local Actions, use this article when the scenario launches an activity and requires overlay permission for the Intune app.

## Before you begin

- Android Enterprise devices must be enrolled as [dedicated devices](../../device-enrollment/android/setup-dedicated) or [fully managed devices](../../device-enrollment/android/setup-fully-managed).
- Supported OEMs include:
    - Samsung (devices running OS 13 and later)
    - Zebra
    - Honeywell
- This article creates OEMConfig configuration profiles in Intune. Before you create OEMConfig profiles, review [OEMConfig profiles in Microsoft Intune - Before you begin](configure-oemconfig-android#before-you-begin) for important information, including the 500-KB file size limit.
- To configure this policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile manager** role. For more information on the built-in roles in Intune, go to [Role-based access control with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Required permissions

Use the following table to decide which app entries to add to the OEMConfig schema.

| App | Scenario | Package name | Permissions covered in this article |
| --- | --- | --- | --- |
| Managed Home Screen (MHS) | MHS features, or Local Actions scenarios that also depend on MHS permissions | `com.microsoft.launcher.enterprise` | Overlay, notification, alarms and reminders, and write settings, depending on OEM support |
| Intune app | Local Actions that launch an activity | `com.microsoft.intune` | Overlay |

If the device uses MHS and also uses Local Actions that launch an activity, grant overlay permission to both apps.

The following table summarizes the permissions supported by the OEMs in this article:

| Permission | Samsung | Zebra | Legacy Zebra | Honeywell |
| --- | --- | --- | --- | --- |
| Overlay | Yes | Yes | Yes | Yes |
| Notification | Yes | Yes | Yes | No |
| Alarms and reminders | Yes | Yes | No | Yes |
| Write settings | Yes | Yes | No | Yes |

For information on when to use Zebra or Legacy Zebra, go to [OEMConfig apps for Zebra devices](deploy-oemconfig-zebra-android#oemconfig-apps-for-zebra-devices).

## Step 1 - Add the OEMConfig app from the Managed Google Play Store

OEMs provide their own OEMConfig app that lets you configure features within the app. In this step, you:

- Get the OEMConfig app from the Managed Google Play Store.
- Assign the app to device groups that use MHS, Local Actions, or both.

Samsung, Zebra, and Honeywell OEMs use the following Managed Google Play apps:

| OEM | App name |
| --- | --- |
| Samsung | Knox Service Plugin |
| Zebra | Zebra OEMConfig Powered by MX Zebra OEMConfig Powered by MX is a new version of the OEMConfig app released in May 2023. |
| Zebra | Legacy Zebra OEMConfig |
| Honeywell | Honeywell UEMConnect |

### Add the OEMConfig app

# [Samsung](#tab/samsung-app)
1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), sign in to your **Managed Google Play account**.
2. Search for the **Knox Service Plugin** app, select the app, and then select **Sync**.

    For the specific steps, go to [Add Managed Google Play apps to Android Enterprise devices with Intune](../../app-management/deployment/add-managed-google-play).
3. In the **Knox Service Plugin** app properties, make it a required app, and assign the app to device groups that need these permissions.

    For the specific steps, go to [Assign an app to groups](../../app-management/deployment/assign-groups#assign-an-app).

# [Zebra](#tab/zebra-mx-app)
1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), sign in to your **Managed Google Play account**.
2. Search for the **Zebra OEMConfig Powered by MX** app, select the app, and then select **Sync**.

    For the specific steps, go to [Add Managed Google Play apps to Android Enterprise devices with Intune](../../app-management/deployment/add-managed-google-play).
3. In the **Zebra OEMConfig Powered by MX** app properties, make it a required app, and assign the app to device groups that need these permissions.

    For the specific steps, go to [Assign an app to groups](../../app-management/deployment/assign-groups#assign-an-app).

# [Zebra Legacy](#tab/zebra-legacy-app)
1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), sign in to your **Managed Google Play account**.
2. Search for the **Legacy Zebra OEMConfig** app, select the app, and then select **Sync**.

    For the specific steps, go to [Add Managed Google Play apps to Android Enterprise devices with Intune](../../app-management/deployment/add-managed-google-play).
3. In the **Legacy Zebra OEMConfig** app properties, make it a required app, and assign the app to device groups that need these permissions.

    For the specific steps, go to [Assign an app to groups](../../app-management/deployment/assign-groups#assign-an-app).

# [Honeywell](#tab/honeywell)
1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), sign in to your **Managed Google Play account**.
2. Search for the **Honeywell UEMConnect** app, select the app, and then select **Sync**.

    For the specific steps, go to [Add Managed Google Play apps to Android Enterprise devices with Intune](../../app-management/deployment/add-managed-google-play).
3. In the **Honeywell UEMConnect** app properties, make it a required app, and assign the app to device groups that need these permissions.

    For the specific steps, go to [Assign an app to groups](../../app-management/deployment/assign-groups#assign-an-app).

---

## Step 2 - Create the OEMConfig profile that grants app permissions

Create one OEMConfig profile per device. In the profile, you use the OEM app schema to grant the permissions required by the app scenario you selected.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **OEMConfig**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **OEMConfig app**: Choose **Select an OEMConfig app**.
    - **Associated app**: Select the OEMConfig app that matches your devices.
6. Select **Next**.

In the OEM app schema, add the app entries that match your scenario. The OEMConfig model only supports one policy per device.

# [Samsung](#tab/samsung-policy)
To grant app permissions by using Samsung Knox Service Plugin, follow these steps:

1. In **Configuration settings**, select **Configuration designer**.

    The properties available within the app schema are shown for you to configure.
2. Use the following guidance to locate the settings that grant special app permissions:

    - [Frontline workers get a better experience from Microsoft and Samsung](https://techcommunity.microsoft.com/t5/microsoft-intune-blog/frontline-workers-get-a-better-experience-from-microsoft-and/ba-p/4078801)
    - [Knox Service Plugin - Grant special permissions for an app](https://docs.samsungknox.com/admin/knox-platform-for-enterprise/knox-service-plugin/kbas/kba-1261-grant-special-permissions-for-an-app/) (opens Samsung's web site)
3. Add the app entries you need:

    - **Managed Home Screen**
        - Package name: `com.microsoft.launcher.enterprise`
        - Notification service package name: `com.microsoft.launcher.enterprise/com.microsoft.launcher.homescreen.next.model.notification.AppNotificationService`
        - Grant the MHS permissions your scenario requires.
    - **Intune app for Local Actions**
        - Package name: `com.microsoft.intune`
        - Grant **Overlay** permission.
4. If the same device uses MHS and Local Actions that launch an activity, configure entries for both apps.
5. Select **Next**, add any [optional scope tags](../../fundamentals/role-based-access-control/scope-tags) &gt; **Next**.
6. In **Assignments**, select the devices or device groups that should receive your profile.

    For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).
7. Select **Next**, and review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time the device checks for configuration updates, the settings you configured are applied to the app.

# [Zebra OEMConfig Powered by MX](#tab/zebra-mx-policy)
To grant app permissions by using Zebra OEMConfig Powered by MX, follow these steps:

Note

On Android 11, the **Zebra OEMConfig Powered by MX** app schema doesn't work if the board support package (BSP) version is `HE_FULL_UPDATE_11-20-18.00-RG-U00-STD-HEL-04`. To use the Zebra OEMConfig Powered by MX app, you must upgrade to a newer BSP.

For more information on updating Zebra devices with Intune, go to [Zebra LifeGuard Over-the-Air Integration with Microsoft Intune](../../device-updates/android/setup-zebra-lifeguard).

1. In **Configuration settings**, select **Configuration designer**.

    The properties available within the app schema are shown for you to configure.
2. Use the following Zebra guidance to locate the settings that grant app permissions:

    - [Enable Notification Access Permission via MDM/EMM OEMConfig 11.9.x.x and Up](https://support.zebra.com/article/000027795) (opens Zebra's web site)
    - [Enabling Display Over Other Apps Permission via MDM/EMM OEMConfig](https://support.zebra.com/article/000021297) (opens Zebra's web site)
    - [Zebra Managed Configurations docs](https://techdocs.zebra.com/oemconfig/15-0/mc2/#pkgConfig.package.packagePermissions.packagePermission) (opens Zebra's web site)
3. Add the app entries you need:

    - **Managed Home Screen**
        - Package name: `com.microsoft.launcher.enterprise`
        - Signing certificate: `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`
        - Grant the MHS permissions your scenario requires.
    - **Intune app for Local Actions**
        - Package name: `com.microsoft.intune`
        - Grant **Overlay** permission.
        - Signing certificate: `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`
4. If the same device uses MHS and Local Actions that launch an activity, configure entries for both apps.
5. Select **Next**, add any [optional scope tags](../../fundamentals/role-based-access-control/scope-tags) &gt; **Next**.
6. In **Assignments**, select the devices or device groups that should receive your profile.

    For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).
7. Select **Next**, and review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time the device checks for configuration updates, the settings you configured are applied to the app.

# [Legacy Zebra OEMConfig](#tab/zebra-legacy-policy)
To grant app permissions by using Legacy Zebra OEMConfig, follow these steps:

1. In **Configuration settings**, select **Configuration designer**.

    The properties available within the app schema are shown for you to configure.
2. Use the following Zebra guidance to locate the settings that grant app permissions:

    - [Enabling Display Over Other Apps Permission via MDM/EMM OEMConfig](https://support.zebra.com/article/000021297)
    - [Enable Notification Access Permission via MDM/EMM OEMConfig 11.5.x.x](https://support.zebra.com/article/000027795)
3. Add the app entries you need:

    - **Managed Home Screen**
        - Package name: `com.microsoft.launcher.enterprise`
        - Signing certificate: `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`
        - Grant **Overlay** and **Notification** permissions.
    - **Intune app for Local Actions**
        - Package name: `com.microsoft.intune`
        - Grant **Overlay** permission.
        - Signing certificate: `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`
4. If the same device uses MHS and Local Actions that launch an activity, configure entries for both apps.
5. Select **Next**, add any [optional scope tags](../../fundamentals/role-based-access-control/scope-tags) &gt; **Next**.
6. In **Assignments**, select the devices or device groups that should receive your profile.

    For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).
7. Select **Next**, review your settings, and then select **Create**.

The next time the device checks for configuration updates, the settings you configured are applied to the app.

# [Honeywell](#tab/honeywell-policy)
To grant app permissions by using Honeywell UEMConnect, follow these steps:

1. In **Configuration settings**, select **Configuration designer**.

    The properties available within the app schema are shown for you to configure.
2. Use the following Honeywell guidance to locate the settings that grant app permissions:

    - [How to Grant Runtime Permissions via OEM Config (Honeywell UEMConnect)](https://sps-support.honeywell.com/s/article/How-to-Grant-Runtime-Permissions-via-OEM-Config-Honeywell-UEMConnect)
3. Add the app entries you need:

    - **Managed Home Screen**
        - Package name: `com.microsoft.launcher.enterprise`
        - Grant the MHS permissions your scenario requires.
    - **Intune app for Local Actions**
        - Package name: `com.microsoft.intune`
        - Grant **Overlay** permission.
4. If the same device uses MHS and Local Actions that launch an activity, configure entries for both apps.
5. Select **Next**, add any [optional scope tags](../../fundamentals/role-based-access-control/scope-tags) &gt; **Next**.
6. In **Assignments**, select the devices or device groups that should receive your profile.

    For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).
7. Select **Next**, and review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time the device checks for configuration updates, the settings you configured are applied to the app.

---