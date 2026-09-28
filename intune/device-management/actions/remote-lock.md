---
layout: Conceptual
title: 'Device Action: Remote Lock - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/remote-lock
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
description: Use the remote lock action in Microsoft Intune to lock a managed device that has a passcode or PIN.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: bf632d5b-6209-46d2-8c9c-8d76b1f704cc
locale: en-us
document_id: c94a2da0-8040-b7e0-ce9a-6c3c155900db
document_version_independent_id: c94a2da0-8040-b7e0-ce9a-6c3c155900db
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/remote-lock.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/remote-lock
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/remote-lock.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5c69d5bf-3918-ea77-8c9f-27bf0f3a1956
---

# Device Action: Remote Lock - Microsoft Intune | Microsoft Learn

The *remote lock* device action locks a managed device so the user must enter the existing passcode or PIN to continue. Use this action when a device is misplaced, left unattended, or suspected of unauthorized use without wiping data or removing enrollment.

Important

Remote lock is only effective if a passcode or PIN is already set:

- If no passcode exists, the screen may just turn off and the user can still access the device.
- Enforce a passcode policy before relying on this action.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated (COSU)
> - Android Enterprise corporate-owned fully managed (COBO)
> - Android Enterprise corporate-owned work profile (COPE)
> - Android Open Source Project (AOSP)
> - iOS/iPadOS
> - macOS
> - visionOS 2.0+
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, at a minimum, use an account that has one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Remote lock**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to remote lock a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remote lock**.

::: zone pivot="macos"

1. Set a six-digit recovery PIN.

Note

The recovery PIN is shown on the device overview pane for up to 30 days, or until another device action is sent. Record it securely; it can't be retrieved afterward. Don't resend remote lock to the same macOS device until that PIN is used—additional attempts show a **Failed** status in reporting.

::: zone-end

## Reference links

- Microsoft Graph API: [remoteLock action](/en-us/graph/api/intune-devices-manageddevice-remotelock)