---
layout: Conceptual
title: Manage Android Enterprise System Apps in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/manage-system-apps-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Android
- FocusArea_Apps_Add
ms.subservice: apps
description: Learn how to manage Android Enterprise system apps in Microsoft Intune.
ms.date: 2025-08-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: priyar
locale: en-us
document_id: b70e3b83-4b03-5f12-16c5-da8f1c11180e
document_version_independent_id: b70e3b83-4b03-5f12-16c5-da8f1c11180e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/manage-system-apps-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/manage-system-apps-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/manage-system-apps-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 0a80f67f-9ea9-1742-0e12-3f63c96ffe12
---

# Manage Android Enterprise System Apps in Microsoft Intune - Microsoft Intune | Microsoft Learn

Before you assign an Android Enterprise system app to a device, you must first enable the app in Microsoft Intune. System apps are supported on Android Enterprise devices. You can enable a system app for [Android Enterprise dedicated devices](../../device-enrollment/android/setup-dedicated), [fully managed devices](../../device-enrollment/android/setup-fully-managed), [Android Enterprise corporate-owned with work profile](../../device-enrollment/android/setup-corporate-work-profile), or [Android Enterprise personally owned work profiles](../protection/mam-vs-work-profiles-android). When you no longer need the system app, you can disable it. Android Enterprise system apps will enable or disable apps that are already part of the platform. To enable an app, assign the system app as **Required**. To disable an app, assign the system app as **Uninstall**. System apps can't be assigned as available for a user.

## Enable a system app in Intune

You can enable an Android Enterprise system app in Intune using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the available **Other** types, select **Android Enterprise system app**.
4. Click **Select**. The **Add app** steps are displayed. In the **App information**page, add the app details:
    - **App Name**: Enter the name of the app.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Package Name**: Enter a package name. Intune will validate that the package name is valid.
5. Click **Next** to display the **Scope tags** page.
6. Click **Select scope tags** to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
7. Click **Next** to display the **Assignments** page.
8. Select the group assignments for the app. To enable the app, assign the app as **Required**. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).
9. Click **Next** to display the **Review + create** page. Review the values and settings you entered for the app.
10. When you're done, click **Create** to enable the app in Intune.

The **Overview** blade of the app you've created is displayed.

Note

You'll need to work with the OEM of your device to find the package name of the app you would like to enable/disable.

You can't create an Android Enterprise system app when there's the same app in Managed Google Play in Intune.

The Notes section won't appear for an Android Enterprise system app and isn't editable.

The app you've created is displayed in the apps list, where you can assign it to the groups that you select.

## Disable an existing system app

You can disable an Android Enterprise system app in Intune using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps**.
3. Select the system app from the app list.
4. Change the assignment for the app to **Uninstalled** and save.

## Disable a new system app

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Android** &gt; **Create**.
3. In **Select app type**, select **Other** &gt; **Android Enterprise system app**.
4. Click **Select**. In **App information**, add the app details:

    - **App Name**: Enter the name of the app.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Package Name**: Enter a package name, like `com.microsoft.word`. Intune validates that the package name is valid.

    For example, to disable the on-device AI experience, you can block the AICore system service by entering the following:

    - **Name**: Enter `AICore`.
    - **Publisher**: Enter `Google Android`.
    - **Package Name**: Enter `com.google.android.aicore`.
5. Select **Next**.
6. Click **Select scope tags** to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
7. In **Assignments** &gt; **Uninstall**, select the group assignments for the app. When you select **Uninstall**, the app is disabled.

    For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).
8. Select **Next**. In **Review + create**, review the values and settings you entered for the app. When you're done, select **Create** to disable the app in Intune.