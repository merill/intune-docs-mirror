---
layout: Conceptual
title: How to Wipe Only Corporate Data From Apps - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/wipe-corporate-data
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Learn how to selectively wipe only corporate data from Intune-managed apps with Microsoft Intune.
ms.date: 2024-06-12T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: bryanke
locale: en-us
document_id: d07b91da-2fbd-c792-6673-787a685ff0e9
document_version_independent_id: d07b91da-2fbd-c792-6673-787a685ff0e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/wipe-corporate-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/wipe-corporate-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/wipe-corporate-data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 26a6add7-87de-a82b-ef56-e4652ef56a37
---

# How to Wipe Only Corporate Data From Apps - Microsoft Intune | Microsoft Learn

When a device is lost or stolen, or if the employee leaves your company, you want to make sure company app data is removed from the device. But you might not want to remove personal data on the device, especially if the device is an employee-owned device.

Note

The iOS/iPadOS, Android, and Windows platforms are the only platforms currently supported for wiping corporate data from Intune managed apps. Intune managed apps are applications that include the Intune App SDK, and have at least one enabled and licensed user account in your organization. Deployment of Application Protection Policies is required to enable app selective wipe on Android and iOS.

Note

For iOS 16 and later devices, the "Device Name" value for all selective wipe actions and status will be a generic device name. For more information, see [Apple Developer documentation](https://developer.apple.com/documentation/uikit/uidevice/1620015-name).

To selectively remove company app data, create a wipe request by using the steps in this article. After the request is finished, the next time the app runs on the device, company data is removed from the app. In addition, you can also configure a selective wipe of your company data as a new action when the conditions of Application Protection Policies Access settings aren't met. This feature helps you automatically protect and remove sensitive company data from applications based on preconfigured criteria.

Important

Contacts synced directly from the app to the native address book are removed. Any contacts synced from the native address book to another external source can't be wiped. Currently, this only applies to the Microsoft Outlook app.

## Create a device based wipe request

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **App selective wipe** &gt; **Create wipe request**.

    The **Create wipe request** pane is displayed.
3. Click **Select user**, choose the user whose app data you want to wipe, and click **Select** at the bottom of the **Select user** pane.

    ![Screenshot of the 'Select user' pane](media/wipe-corporate-data/apps-selective-wipe-01.png)
4. Click **Select the device**, choose the device, and click **Select** at the bottom of the **Select Device** pane.

    ![Screenshot of 'Create wipe request' pane where device is selected](media/wipe-corporate-data/apps-selective-wipe-02.png)
5. Click **Create** to make a wipe request.

The service creates and tracks a separate wipe request for each protected app on the device, and the user associated with the wipe request.

![Screenshot of 'Client apps - App selective wipe' pane](media/wipe-corporate-data/apps-selective-wipe-03.png)

## Create a user based wipe request

By adding a user to the User-level wipe you'll automatically issue wipe commands to all apps on all the user's devices. The user will continue to get wipe commands at every check-in from all devices. To re-enable a user, you must remove them from the list.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **App selective wipe** &gt; **User-Level Wipe**
3. Select **Add**. The **Select user** pane displays.
4. Choose the user whose app data you would like to wipe &gt; **Select**.

## Monitor your wipe requests

You can have a summarized report that shows the overall status of the wipe request, and includes the number of pending requests and failures. Completed wipe request entries remain in the report for 4 days after completion. In the event that a wipe request is not marked as completed, but remains in a pending state, the request remains in the report for a total number of days equal to the sum of the value of Offline grace period wipe data + 4 days for the record to be deleted which, by default, is 94 days.

To get more details, follow these steps:

1. On the **Apps** &gt; **App selective wipe** pane, you can see the list of your requests grouped by users. Because the system creates a wipe request for each protected app running on the device, you might see multiple requests for a user. The status indicates whether a wipe request is **pending**, **failed**, or **successful**.

    ![Screenshot of the wipe request status in the App selective wipe pane.](media/wipe-corporate-data/wipe-request-status-1.png)

Additionally, you're able to see the device name, and its device type, which can be helpful when reading the reports.

Important

The user must open the app for the wipe to occur, and the wipe may take up to 30 minutes after the request was made.

## Delete a device wipe request

Wipes with pending status are displayed until you manually delete them. To manually delete a wipe request:

1. On the **Client Apps - App selective wipe** pane.
2. From the list, right-click on the wipe request you want to delete, then choose **Delete wipe request**.

    ![Screenshot of the wipe request list in the App selective wipe pane](media/wipe-corporate-data/delete-wipe-request.png)
3. You're prompted to confirm the deletion, choose **Yes** or **No**, then click **OK**.

## Delete a user wipe request

User wipes will remain in the list until removed by an administrator. To remove a user from the list:

1. On the **Client Apps - App selective wipe** pane select **User-Level Wipe**
2. From the list, right-click on the user you want to delete, then choose **Delete**.