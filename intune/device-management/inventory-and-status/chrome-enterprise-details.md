---
layout: Conceptual
title: View ChromeOS device information - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/chrome-enterprise-details
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: View ChromeOS devices and details synced with the Chrome Enterprise connector in the Microsoft Intune admin center.
ms.date: 2023-11-06T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: shsivak
locale: en-us
document_id: 526c3dc5-a9f1-837c-cc9d-7c23553585ae
document_version_independent_id: 526c3dc5-a9f1-837c-cc9d-7c23553585ae
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/inventory-and-status/chrome-enterprise-details.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/inventory-and-status/chrome-enterprise-details
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/inventory-and-status/chrome-enterprise-details.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 084a973d-4797-0930-0aa1-49d220ca7652
---

# View ChromeOS device information - Microsoft Intune | Microsoft Learn

View details about your Chrome Enterprise connector and ChromeOS devices in the Microsoft Intune admin center. Information becomes available after:

- You establish the connection between Google Admin console and Microsoft Intune.
- The initial device sync finishes.
- The status in the admin center shows as **Active**.

You can view synced devices in the **Devices** &gt; **All devices** list and throughout the admin center where Intune-managed devices are shown. This article describes the information available, which you can use for monitoring or reporting, and where to find it in the admin center.

## Prerequisites

To view ChromeOS devices and device details, you must be assigned a role with *read* permission for *Chrome Enterprise*.

Devices must be enrolled before you can see them in the admin center. Enrollment for ChromeOS devices is done in the Google Admin center. You can create the connection before or after you enroll devices. For more information, see [Enroll ChromeOS devices in Google Admin console](https://support.google.com/chrome/a/answer/1360534) (opens Chrome Enterprise and Education Help).

## View ChromeOS devices

Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices** &gt; **All devices** to view an aggregated list of all devices in Intune, including those running ChromeOS. The following information is shown for ChromeOS devices:

- **Device name**: Device names for ChromeOS devices appear as `Chrome- {serialNumber}`.
- **Managed by**: ChromeOS devices are managed by **Intune**.
- **Ownership**: ChromeOS devices are always marked as **Corporate**.
- **Compliance**: Compliance policies aren't supported with ChromeOS devices in Intune, so they appear in this column as **Not evaluated**.

Select **Filter** to filter the device list by platform. You can also go to the navigation menu and select **ChromeOS** for an exclusive view of ChromeOS devices.

## View ChromeOS device details

Directly select a device to view more details about it. The device's **Overview** page shows the device name, and lists key properties of the device, such as ownership, serial number, primary user, and device model.

You can also view properties and system info for a device, as described in the following sections.

### Properties

Select **Properties** to view management information about the device.

The following properties sync back to the Google Admin console. Any changes made to these properties in Intune also show up in the Google Admin console.

- Management name, known in Google Admin as the *asset ID*
- User
- Location
- Notes

### System info

Select **System info** to see a real-time snapshot of the information available from the Google Admin console.

### Delegated administration

You can create dynamic device groups based on a [Google Admin organizational unit](https://knowledge.workspace.google.com/kb/how-to-create-an-organizational-unit-000007002) as a way to delegate administrators to Intune-synced ChromeOS devices. This section describes how to create a dynamic device group so that you can control admin access to the ChromeOS device inventory and remote device actions in the Microsoft Intune admin center.

1. In the Microsoft Intune admin center, [create a group](../../fundamentals/tenant-administration/add-groups#add-groups-to-intune) with the following details:

    1. For **Membership type**, select **Dynamic Device**.
    2. Select **Add a dynamic query**.
    3. For **Property**, select **enrollmentProfileName**. Select the **Operator**, depending on how you want the rule to work. For **Value**, enter the name of a Google Admin organizational unit.
2. Create a scope tag for an Intune RBAC role. The scope tag determines the level of access for the Intune role. When you get to **Assignments**, include the dynamic device group you previously created. For more information, see [Use role-based access (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags#to-create-a-scope-tag).

    After you save the scope tag, it applies to every device that's part of the dynamic device group. The organizational unit's information syncs with the *enrollmentProfileName* device object property in Microsoft Entra ID, using the full path format shown in System info.

    For example: `/OU Level1/OU Level2`.

    The maximum length of the string is 255 characters. Intune truncates the first part of the string if it exceeds the max number of characters.

    For example: `/OU Level1/OU Level2/.../OU Level18` becomes `evel1/OU Level2/.../OU Level18`.