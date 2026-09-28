---
layout: Conceptual
title: Add iOS Store Apps to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-store-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- iOS/iPadOS
- FocusArea_Apps_Store
ms.reviewer: bryanke
ms.subservice: apps
description: Learn about adding iOS store apps to Microsoft Intune. You can assign apps using this method if the apps are free of charge in the App Store.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 44501f85-81c2-8a83-7d25-183b0c55a0de
document_version_independent_id: 44501f85-81c2-8a83-7d25-183b0c55a0de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-store-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-store-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-store-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: aa20c0a8-cf30-1b32-5b8d-25379173c0de
---

# Add iOS Store Apps to Microsoft Intune - Microsoft Intune | Microsoft Learn

Use the information in this article to help you add iOS store apps to Microsoft Intune. iOS store apps are apps that Intune installs on your users' devices. A user is part of your company's workforce. iOS store apps are automatically updated.

Note

Although users of iOS/iPadOS devices can remove some built-in iOS/iPadOS apps, such as Stocks and Maps, you cannot use Intune to redeploy those apps. If your users delete these apps, they must go to the App Store and manually reinstall them.

## Before you start

You can assign apps by using this method only if they are free of charge in the App Store. If you want to assign paid apps by using Intune, consider using the [iOS/iPadOS volume-purchase program](manage-vpp-apple).

Note

When you work with Microsoft Intune, we recommend that you use either the Microsoft Edge or Google Chrome browser.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the available **Store app** types, select **iOS store app**.
4. Click **Select**. The **Add app** steps are displayed.
5. Select **Search the App Store**.
6. In the **Search the App Store** pane, select the App Store country/region locale.
7. In the **Search** box, type the name (or part of the name) of the app. Intune searches the store and returns a list of relevant results.
8. In the results list, select the app you want, and then select **Select**.

    The **App information** page will be displayed in the **Add app** pane. When possible, app information will be added based on the app you selected from the store.
9. In the **App information** page, add the app details. Depending on the app you have chosen, some of the values in this pane might have been automatically filled in:

    - **Name**: Enter the name of the app as it is to be displayed in the company portal. Make sure that any app name that you use is unique. If an app name is duplicated, only one name is displayed to users in the company portal.
    - **Description**: Enter a description for the app. This description is displayed to users in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Appstore URL**: Type the App Store URL of the app that you want to create.
    - **Minimum operating system**: In the list, select the earliest operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.
    - **Applicable device type**: In the list, select the devices that are used by the app.
    - **Category**: Optionally, select one or more of the built-in app categories, or a category that you created. Doing so makes it easier for users to find the app when they browse the company portal.
    - **Show this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Optionally, enter the name of the app developer. This field is visible only to administrators and is not visible to your users.
    - **Owner**: Optionally, enter a name for the owner of this app, for example, *HR department*. This field is visible only to administrators and is not visible to your users.
    - **Notes**: Optionally, enter any notes that you want to associate with this app. This field is only visible an administrator and will not be visible to end users.
    - **Logo**: Optionally, upload an icon that will be associated with the app. This icon is displayed with the app when users browse the company portal.
10. Click **Next** to display the **Scope tags** page.
11. Click **Select scope tags** to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
12. Click **Next** to display the **Assignments** page.
13. Select the group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).
14. Click **Next** to display the **Review + create** page. Review the values and settings you entered for the app.
15. When you are done, click **Create** to add the app to Intune.

The **Overview** blade of the app you've created is displayed.