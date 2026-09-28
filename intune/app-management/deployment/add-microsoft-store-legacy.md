---
layout: Conceptual
title: Add Microsoft Store Apps to Intune (Legacy) - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-microsoft-store-legacy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Store
ms.reviewer: bryanke
ms.subservice: apps
description: Learn about adding Microsoft Store (legacy) apps to Intune.
ms.date: 2024-04-17T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 00ed1ee3-4ed0-64da-4d0a-daa8b94ea6f1
document_version_independent_id: 00ed1ee3-4ed0-64da-4d0a-daa8b94ea6f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-microsoft-store-legacy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-microsoft-store-legacy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-microsoft-store-legacy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: b5b2666d-08a8-1ed4-8ea8-0990d1637e7e
---

# Add Microsoft Store Apps to Intune (Legacy) - Microsoft Intune | Microsoft Learn

Before you can assign, monitor, configure, or protect apps, you must add them to Intune.

Important

The steps provided in this topic refer to adding Microsoft Store apps using the legacy method. For the latest method, see [Add Microsoft Store apps to Microsoft Intune](add-microsoft-store).

## Add an app to Intune

You can add a Microsoft Store app to Intune by doing the following:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the available **Store app** types, select **Microsoft store app (Legacy)**.
4. Click **Select**. The **Add app** steps are displayed.
5. To configure the **App information** for Microsoft store apps, click **Select app**, and search for the app you want to assign to members of your organization. Display the app page and make a note of the app details.
6. In the **App information**page, add the app details:
    - **Name**: Enter the name of the app as it is to be displayed in the company portal. Make sure that any app name that you use is unique. If an app name is duplicated, only one name is displayed to users in the company portal.
    - **Description**: Enter a description for the app. This description is displayed to users in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Appstore URL**: Enter the 'Link for Intune' URL for the app provided by the store.
    - **Category**: Optionally, select one or more of the built-in app categories, or a category that you created. Doing so makes it easier for users to find the app when they browse the company portal.
    - **Show this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps.
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

The app that you've created is displayed in the apps list, where you can assign it to the groups that you select.

Important

Microsoft Store apps can only be assigned to groups with the assignment type **Available for enrolled devices** (users install the app from the Company Portal app or website).