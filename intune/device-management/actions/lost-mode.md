---
layout: Conceptual
title: 'Device Action: Lost Mode - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.reviewer: mattcall
ms.subservice: remote-actions
zone_pivot_group_filename: device-management/actions/zone-pivot-groups.json
description: Learn how to enable Lost Mode in Microsoft Intune to remotely lock a lost or stolen iOS or iPadOS device and display a custom message and phone number on the lock screen.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 46b8d067-28e2-43a6-97b2-ffcc8414e503
locale: en-us
document_id: 748ff859-980f-6c17-57b8-8389d79c93a3
document_version_independent_id: 748ff859-980f-6c17-57b8-8389d79c93a3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/lost-mode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/lost-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/lost-mode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: f0ff9fc1-29f9-cbe5-a1c3-81e6c683252a
---

# Device Action: Lost Mode - Microsoft Intune | Microsoft Learn

The *Lost Mode* device action in Microsoft Intune allows IT administrators to remotely lock and track lost or stolen devices. When activated, Lost Mode displays a custom message and contact phone number on the device's lock screen—helping facilitate recovery while protecting corporate data.

::: zone pivot="ios"

Once enabled, the device is locked and can't be accessed until Lost Mode is disabled by an administrator. While in Lost Mode, the device's location can also be tracked with the **[Locate device](locate)** action, making it easier to recover.

::: zone-end

::: zone pivot="chromeos"

Chrome Enterprise and the Google Admin console refer to devices in lost mode as *disabled*. For more information about how to disable a device, see the Chrome Enterprise and Education Help documentation.

::: zone-end

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - iOS/iPadOS in [Supervised Mode](../../device-enrollment/apple/enable-supervised-mode)
> - ChromeOS
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, at a minimum, use an account that has one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permissions **Remote tasks/Enable lost mode**, **Remote tasks/Disable lost mode**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to enable Lost Mode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Lost mode (supervised only)**.
4. Under **Lost mode**, select **Enable**.
5. In the **Message to display on lock screen**, type a message to display on the device's lock screen.
6. Optionally, enter a phone number in the **Phone number to display** box.
7. Select **OK** to save your changes.

Tip

In the message you enter to show on the lock screen, include specific details to return the lost device.

## User experience

When you enable Lost Mode, the device is locked. The custom message and phone number you specify are displayed on the lock screen, helping facilitate recovery. While Lost Mode is active, the user can't access the device.

::: zone pivot="ios"

To locate the device during this time, use the [Locate device](locate) action in the admin center.

Note

Some built-in device functionalities might still work. For example, Siri might still be used to make calls unless it's disabled.

## How to disable Lost Mode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device, and then **Lost mode (supervised only)**.
3. Under **Lost mode**, select **Disable**.
4. Select **OK** to save your changes.

::: zone-end

## Reference links

- Microsoft Graph API:
    - [enableLostMode action](/en-us/graph/api/intune-devices-manageddevice-enablelostmode)
    - [disableLostMode action](/en-us/graph/api/intune-devices-manageddevice-disablelostmode)