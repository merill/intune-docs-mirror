---
layout: Conceptual
title: 'Device Action: Sync - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/sync
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
description: Learn how to use the device sync action in Intune to apply policy, app, and configuration updates to managed devices.
ms.date: 2026-08-06T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
zone_pivot_groups: 51e33912-415a-402f-8201-8acebf3e4991
locale: en-us
document_id: ddbd81da-9553-80b5-c9c3-bb511af670e1
document_version_independent_id: ddbd81da-9553-80b5-c9c3-bb511af670e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/sync.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/sync
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/sync.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: f76dc147-9efb-f7f0-41cf-986b5742aa13
---

# Device Action: Sync - Microsoft Intune | Microsoft Learn

The *sync* device action forces a device to check in with Intune. When a device checks in, it receives any pending actions or policies assigned to it. This action is useful for validating and troubleshooting policy deployment without waiting for the next scheduled check-in.

For more information about the standard Intune policy check-in frequencies, see [Refresh cycle times](../../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - tvOS
> - visionOS
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Sync devices**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## Sync a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Sync**.
4. To confirm, select **Yes**.

::: zone pivot="windows"

## Sync behavior on Windows

After selecting **Sync**, Intune initiates an on-demand synchronization across multiple workloads to help ensure the device reflects the latest admin intent as quickly as possible. This process includes, but isn't limited to:

- Configuration policy processing
- App detection and deployment state updates
- Script and remediation processing
- Other device management signals required to align device state with current assignments

You can track the progress of the sync action by selecting the **Device sync status** tab in the device overview pane.

Note

The described sync behavior, including the **Device sync status** tab, applies only to Windows and iOS/iPadOS devices. To see the new device sync improvements, ensure that the 'Preview new device view' toggle is turned ON. This is at the top right of the Intune admin console screen.

::: zone-end

::: zone pivot="ios"

## Sync behavior on iOS/iPadOS

After selecting **Sync**, Intune initiates an on-demand synchronization across multiple workloads to help ensure the device reflects the latest admin intent as quickly as possible. This process includes, but isn't limited to:

- Configuration policy processing
- App detection and deployment state updates
- Script and remediation processing
- Other device management signals required to align device state with current assignments

You can track the progress of the sync action by selecting the **Device sync status** tab in the device overview pane.

Note

The described sync behavior, including the **Device sync status** tab, applies only to iOS/iPadOS and Windows devices. To see the new device sync improvements, ensure that the 'Preview new device view' toggle is turned ON. This is at the top right of the Intune admin console screen.

::: zone-end

::: zone pivot="ios,android"

## Retryable error codes

When you run the **Sync** action, apps that fail and raise a retryable error code remain available to the device. Apps that raise a nonretryable error code must wait seven days before they're available to the device.

| Error code | Suggested description | Retryable |
| --- | --- | --- |
| 2016330898 | An unknown error occurred. | No |
| 2016330897 | Your connection to Intune timed out. Reset your connection. | Yes |
| 2016330896 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330895 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330894 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330893 | You lost connection to the Internet. Reset your connection. | Yes |
| 2016330892 | International roaming is disabled. | No |
| 2016330891 | The cellular data connection for this device can't be accessed while a phone call is being made. Wait for the phone call to complete. | Yes |
| 2016330890 | The cellular network for this device. These devices couldn't be used at this time. | No |
| 2016330889 | The secure connection failed. Reset your connection. | Yes |
| 2016330888 | The server trust evaluation has failed. | No |

::: zone-end

## Reference links

- Microsoft Graph API: [syncDevice action](/en-us/graph/api/intune-devices-manageddevice-syncdevice)