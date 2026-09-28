---
layout: Conceptual
title: Configure ChromeOS connector for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/configure-chrome-enterprise-connector
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Learn how to connect the Google Admin Console to Microsoft Intune so that you can view and take action on enrolled ChromeOS devices.
ms.date: 2022-10-26T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: shsivak
locale: en-us
document_id: f2543475-67e6-6a2a-bcc5-0e739b4bbd29
document_version_independent_id: f2543475-67e6-6a2a-bcc5-0e739b4bbd29
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/configure-chrome-enterprise-connector.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/configure-chrome-enterprise-connector
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/configure-chrome-enterprise-connector.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 660bfd82-8702-7d08-a54a-67b311daedff
---

# Configure ChromeOS connector for Microsoft Intune - Microsoft Intune | Microsoft Learn

Set up the Chrome Enterprise connector with Microsoft Intune to view and take action on company and school-owned ChromeOS devices. This article describes how to create and monitor a connection between the Google Admin console and Microsoft Intune. After you establish a connection, you can:

- Sync device information between the Google Admin console and Microsoft Intune.
- View device information in your device inventory lists in the Microsoft Intune admin center.
- Apply remote actions, such as deprovision, restart, lost mode, and wipe in the admin center.

One connection is allowed per tenant.

Devices must be enrolled before you can see them in the admin center. Enrollment for ChromeOS devices is done in the Google Admin center. You can create the connection before or after you enroll devices. For more information, see [Enroll ChromeOS devices](https://support.google.com/chrome/a/answer/1360534) (opens Chrome Enterprise and Education Help).

## Prerequisites

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To establish a connection, you must have:
> 
> - Access to the Google Admin console and [permission to manage ChromeOS devices](https://support.google.com/a/answer/9807615)
> - One of these roles:
>     - **Intune Service Administrator**
>     - Custom Intune role with *Chrome Enterprise update connection settings* permission
> 

## Create Chrome Enterprise connection

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Tenant administration** &gt; **Connectors and tokens**.
3. Select **Chrome Enterprise** &gt; **Connect**.
4. On the **Connect to Chrome Enterprise** page, select **Google Admin console**, and then:

    1. Sign in to the Admin console.
    2. Go to **Security** &gt; **Access and data control** &gt; **API Controls**.
    3. Select **MANAGE DOMAIN WIDE DELEGATION**.
    4. Select **Add new** to create the API client for your connection.
    5. In the Microsoft Intune admin center, copy the Client ID and OAuth Scopes.
    6. Return to the Google Admin console and paste each value in the **Client ID** and **OAutho scopes (comma-delimited)** spaces, respectively. Intune requires the following scopes: `https://www.googleapis.com/auth/admin.directory.device.chromeos``https://www.googleapis.com/auth/admin.directory.user.readonly``https://www.googleapis.com/auth/admin.directory.orgunit.readonly`
    7. Select **Authorize** to save all changes.
5. Return to the Microsoft Intune admin center and select **Launch Google to connect now.**
6. When prompted to authenticate with your organization's Google Enterprise domain, use your Google Admin account. The Google Admin account appears in Google Workspace audit logs for all actions applied to ChromeOS devices in the Intune admin center. Your account must have:

    - Permission to manage ChromeOS devices, as described in [Prerequisites](configure-chrome-enterprise-connector#prerequisites).
    - Access to Google Workspace Admin SDK Directory API.

After you authenticate, the connection is established and your organization's enrolled ChromeOS devices begin syncing from the Google Admin console. The status changes to **Active** when syncing is complete.

Note

Sync time varies and depends on the number of ChromeOS devices you have in the Google Admin console.

## Monitor connection status

Go to **Chrome Enterprise** in the Microsoft Intune admin center to check the overall health of your connection, and get details about the ongoing and completed syncs. ChromeOS devices should appear shortly after the initial connection. Devices will continue to sync periodically and receive updates.

Available details include:

- **Status**: **Syncing** is shown when devices are still being synced. The status changes to **Active** when syncing is complete.
- **Last check-in**: Shows the last time new devices, device details, or remote actions were synced between Microsoft Intune and the Google Admin console.
- **Chrome devices synced**: Shows the number of ChromeOS devices synced with Intune.
- **Connected account**: Shows the Google Admin account that's connected to Microsoft Intune.

## Delete connection

These roles can delete the connection between Microsoft Intune and the Google Admin console:

- Intune Service Administrator
- Custom Intune role that has *Chrome Enterprise delete connection settings permission*

Deleting your connection removes all ChromeOS devices and Chrome Enterprise connection settings from Intune and Microsoft Entra ID. After the existing connection is deleted, you'll have space in your tenant to create a new connection.

To delete the connection in the Microsoft Intune admin center:

1. Go to **Tenant administration** &gt; **Connectors and tokens**.
2. Select **Chrome Enterprise**.
3. Select **Delete**.