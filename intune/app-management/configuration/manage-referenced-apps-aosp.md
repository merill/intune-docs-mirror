---
layout: Conceptual
title: Manage AOSP Referenced Apps in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/manage-referenced-apps-aosp
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: abigail-stein2
ms.author: abigailstein
ms.collection:
- M365-identity-device-management
- Android
- FocusArea_Apps_Add
ms.subservice: apps
description: Add AOSP referenced apps by package name in Microsoft Intune. Assign Required or Uninstall intent to unhide or hide device-resident apps.
ms.topic: how-to
ms.date: 2026-10-21T00:00:00.0000000Z
ms.custom: msecd-doc-authoring-1030
ai-usage: ai-generated
locale: en-us
document_id: fcb224d1-6103-7da5-a8e7-371be3a7b0e3
document_version_independent_id: fcb224d1-6103-7da5-a8e7-371be3a7b0e3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/manage-referenced-apps-aosp.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/manage-referenced-apps-aosp
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/manage-referenced-apps-aosp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 8acfdbc9-4ac4-1ae5-b6e8-9d940fed12e2
---

# Manage AOSP Referenced Apps in Microsoft Intune - Microsoft Intune | Microsoft Learn

AOSP referenced apps identify apps by package name instead of an uploaded APK. You can use Microsoft Intune to manage OEM, preloaded, or externally deployed apps on Android Open Source Project (AOSP) devices. The app must already be on the device or be deployed outside Intune.

To unhide an existing app on the device, assign the referenced app as **Required**. To hide the app without deleting it, assign it as **Uninstall**. The **Available** assignment type isn't supported for referenced apps.

AOSP referenced apps support user-associated and userless AOSP devices.

## Before you start

- Make sure the devices are enrolled in Intune with AOSP user-associated or AOSP userless enrollment.
- Make sure the app is already on the devices, or arrange to deploy it outside Intune.
- Get the app's package name. If you don't know the package name, contact the device manufacturer or app vendor.
- Make sure you have permissions to create and assign apps in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). For permission guidance, see [Role-based access control](../../fundamentals/role-based-access-control/overview).

## Select the app type

Select the AOSP referenced app type to open the app creation steps. You don't need to upload an APK or select an app from Google Play.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All apps** &gt; **Create**.
3. For **Platform**, select **Android**.
4. For **Category**, select **Referenced apps**.
5. Select **AOSP referenced app**, and then select **Create**.

## Set app information

Enter the app details and the package name that Intune uses to identify the app on the device.

1. On the **App information**page, add the following details:
    - **Name**: Enter the name of the app as it appears in Intune.
    - **Publisher**: Enter the name of the app publisher.
    - **Package name**: Enter the package name of the app. Intune validates that the package name is valid.
2. Select **Next** to display the **Scope tags** page.

The package name can't be changed after you create the app. To manage a different package, create a new referenced app. If you don't know the package name, contact the device manufacturer or app vendor.

You can't create referenced apps for Company Portal (`com.microsoft.windowsintune.companyportal`) or Microsoft Authenticator (`com.azure.authenticator`).

## Select scope tags (optional)

Use scope tags to control which administrators can access the app in Intune. For more information, see [Use role-based access control and scope tags](../../fundamentals/role-based-access-control/scope-tags).

1. Select **Select scope tags** to add scope tags for the app, if needed.
2. Select **Next** to display the **Assignments** page.

## Assign the app

Choose group assignments to unhide or hide the app on targeted devices. AOSP referenced apps support **Required** and **Uninstall** assignments only.

- **Required**: Unhides an existing, enabled app when needed. If a preinstalled system package is retained on the device but isn't installed for the current user, Intune can restore it for that user. Intune doesn't download a new APK. If the package isn't on the device, the assignment fails.
- **Uninstall**: Hides the app without removing its APK or app data, and without disabling it. If the app is absent or already hidden, the assignment is satisfied without further action.

Note

An app's hidden state is separate from its enabled state. Intune can unhide or restore an app, but it can't override a disabled state set by the user, device manufacturer, or another mechanism. A **Required** assignment fails until the app is enabled outside Intune.

1. Select the group assignments under **Required** or **Uninstall**.
2. Select **Next** to display the **Review + create** page.

Note

If an app doesn't have a launchable activity, its icon won't appear on the home screen, even when a **Required** assignment succeeds.

For group assignment guidance, see [Assign apps to groups](../deployment/assign-groups).

## Review and create the app

Review the app details before adding the referenced app to Intune.

1. Review the values and settings on the **Review + create** page.
2. Select **Create** to add the app to Intune.

The app's **Overview** page is displayed. The referenced app also appears in the apps list.

## Hide an existing referenced app

To hide an OEM, preloaded, or externally deployed app, assign the referenced app as **Uninstall**. The app's APK and data remain on the device.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All apps**.
3. Select the AOSP referenced app from the apps list.
4. Select **Properties**, and edit **Assignments**.
5. Add the target group under **Uninstall** and remove its **Required** assignment, if one exists.
6. Review and save the assignments.

If another referenced-app **Required** assignment targets the same package on the device, it takes precedence over **Uninstall**. Removing a Required assignment alone doesn't hide the app.