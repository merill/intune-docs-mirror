---
layout: Conceptual
title: Add Built-In Apps to Mobile Devices Using Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-built-in
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Add
ms.reviewer: bryanke
ms.subservice: apps
description: Learn how you can use Intune to make it easier to install built-in apps mobile devices.
ms.date: 2024-11-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: bf244880-b6d0-1f71-1b17-4b4ad7ac9bc3
document_version_independent_id: bf244880-b6d0-1f71-1b17-4b4ad7ac9bc3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-built-in.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-built-in
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-built-in.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
platformId: 324f14ab-db96-d054-47a3-792e8065e3dc
---

# Add Built-In Apps to Mobile Devices Using Microsoft Intune - Microsoft Intune | Microsoft Learn

The *built-in* app type makes it easy for you to assign curated managed apps, such as Microsoft 365 apps and third-party apps, to iOS/iPadOS and Android devices. You can assign specific apps for this app type, such as Excel, OneDrive, Outlook, Skype, and others. After you add an app, the app type is displayed as either *Built-in iOS app* or *Built-in Android app*. By using the built-in app type, you can choose which of these apps to publish to device users.

Note

Built-in apps are not supported on Android Enterprise devices. For more information about Android Enterprise supported apps, see [Add Managed Google Play apps to Android Enterprise devices with Intune](add-managed-google-play) and [Manage Android Enterprise system apps in Microsoft Intune](../configuration/manage-system-apps-android).

In earlier versions of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), Intune provided several default managed Microsoft 365 apps, such as Outlook and OneDrive. The app types for these managed apps were tagged as *Managed iOS Store App* or *Managed Android App*. Instead of using these app types, we recommend that you use the built-in app type. By using the built-in app type, you have the additional flexibility to edit and delete Microsoft 365 apps.

Note

Default Microsoft 365 apps that are tagged as *Managed iOS Store* and *Managed Android App* are removed from the app list when all assignments are deleted.

## Add a built-in app

To add a built-in app to your available apps in Microsoft Intune, do the following:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the available **Other** types, select **Built-In app**.
4. Click **Select**. The **Add app** steps are displayed.
5. In the **Select Built-in apps** page, click **Select app** to select the apps that you want to include.
6. Select the built-in apps that you want to include.
7. Once you have selected the apps, click **Select** on the **Select Built-in apps** pane.
8. Click **Next** to display the **Scope tags** page.
9. Click **Select scope tags** to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
10. Click **Next** to display the **Assignments** page.
11. Select the group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).
12. Click **Next** to display the **Review + create** page. Review the values and settings you entered for the app.
13. When you are done, click **Create** to add the app to Intune.

    The **Overview** blade of the app you've created is displayed.

## Configure app information

You can modify information about the built-in app. This information helps you to identify the app in Intune and helps users find the app in the company portal.

1. Select **Apps** &gt; **All Apps** and select the built-in app that you want to modify. A pane for the built-in app is displayed.
2. Select **Properties**.
3. Select **Edit** next to **App information**.
4. In the **App information** pane, you can modify the following information:

    - **Name**: Enter the name of the built-in app as it is displayed in the company portal. Make sure all names that you use are unique. If the same app name exists twice, only one of the apps is displayed to users in the company portal.
    - **Description**: Enter a description for the app.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Category**: Optionally, select one or more of the built-in app categories. Setting this option makes it easier for users to find the app when they browse the company portal.
    - **Show this as a featured app in the company portal**: Display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app (for example, *HR department*).
    - **Notes**: Enter any notes that you want to associate with this app.
    - **Upload Icon**: Upload an icon that is displayed with the app when users browse the company portal.
5. Click **Review + save** to display the **Review + create** page. Review the values and settings you entered for the app.
6. When you are done, click **Save** to update the app in Intune.

    The **Overview** blade of the app you've created is displayed.