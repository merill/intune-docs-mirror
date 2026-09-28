---
layout: Conceptual
title: Add Android Store Apps to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-store-android
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
- FocusArea_Apps_Store
ms.reviewer: bryanke
ms.subservice: apps
description: Learn how to add Android store apps from the Google Play store to Microsoft Intune.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: d069e8c7-706c-2809-bdfb-3a0675b59e1e
document_version_independent_id: d069e8c7-706c-2809-bdfb-3a0675b59e1e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-store-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-store-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-store-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a2dbaba9-da88-572d-ee1b-e5b6cbda83b3
---

# Add Android Store Apps to Microsoft Intune - Microsoft Intune | Microsoft Learn

Before you assign an app to a device or a group of users, you must first add the app to Microsoft Intune.

## Add an app

You can add an Android store app to Intune from the portal by doing the following:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the available **Store app** types, select **Android store app**.
4. Click **Select**. The **Add app** steps are displayed.
5. To configure the **App information** for the Android app, navigate to the [Google Play store](https://play.google.com/store) and search for the app you want to deploy. Display the app page and make a note of the app details.
6. In the **App information**page, add the app details:
    - **Name**: Enter the name of the app as it is to be displayed in the company portal. Make sure that any app name that you use is unique. If an app name is duplicated, only one name is displayed to users in the company portal.
    - **Description**: Enter a description for the app. This description is displayed to users in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Appstore URL**: Enter the app store URL of the app that you want to create. Use the URL of the app page when the details of the app are displayed in the store.
    - **Minimum operating system**: In the list, select the earliest operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.
    - **Category**: Optionally, select one or more of the built-in app categories, or a category that you created. Doing so makes it easier for users to find the app when they browse the company portal.
    - **Show this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps. Applies to apps deployed with Available intent.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app, for example, *HR department*.
    - **Notes**: Optionally, enter any notes that you want to associate with this app.
    - **Logo**: Optionally, upload an icon that will be associated with the app. This icon is displayed with the app when users browse the company portal.
7. Click **Next** to display the **Scope tags** page.
8. Click **Select scope tags** to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
9. Click **Next** to display the **Assignments** page.
10. Select the group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).
11. Click **Next** to display the **Review + create** page. Review the values and settings you entered for the app.
12. When you are done, click **Create** to add the app to Intune.

The **Overview** blade of the app you've created is displayed.