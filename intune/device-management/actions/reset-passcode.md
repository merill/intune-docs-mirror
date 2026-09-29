---
layout: Conceptual
title: 'Device Action: Reset Passcode - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/reset-passcode
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
description: Learn how to reset a passcode with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 77015a26-1553-8ca2-2e74-ba61b5f200fa
document_version_independent_id: 77015a26-1553-8ca2-2e74-ba61b5f200fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/reset-passcode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/reset-passcode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/reset-passcode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b466bba9-90eb-36a3-6a53-1a52f06dbe43
---

# Device Action: Reset Passcode - Microsoft Intune | Microsoft Learn

With the *reset passcode* action in Microsoft Intune, you can remotely reset a device passcode to help users regain access to their devices without requiring a full device wipe. this action is especially useful when a user forgets their passcode or is locked out of their device or work profile.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated (COSU)
> - Android Enterprise corporate-owned fully managed (COBO)
> - Android Enterprise corporate-owned work profile (COPE)
> - Android Enterprise personally-owned work profile (BYOD)
> - Android Open Source Project (AOSP)
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote Tasks/Reset Passcode**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## Passcode reset types

When working with Android devices, it's important to understand the two types of passcode resets available:

- **Device-level passcode reset**: The action resets the passcode for the entire device.
- **Work profile passcode reset**: The action resets the passcode for the user's work profile only.

The following table summarizes the passcode reset types based on platform:

| Platform | Device-level passcode reset | Work profile passcode reset |
| --- | --- | --- |
| Android Enterprise corporate-owned dedicated (COSU) | ✅ | ❌ |
| Android Enterprise corporate-owned fully managed (COBO) | ❌ | ✅ |
| Android Enterprise corporate-owned work profile (COPE) | ❌ | ✅ |
| Android Enterprise personally-owned work profile (BYOD) | ❌ | ✅ |
| Android Open Source Project (AOSP) | ✅ | ❌ |

Important

Before initiating a passcode reset, ensure that the passcode requirement is enforced via [device configuration policies](../../device-configuration/settings-catalog/ref-android-settings)—otherwise, the reset fails.

## How to reset a passcode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Secure** &gt; **Reset passcode**.
4. A new passcode is presented to the admin.

The new passcode must be entered on the device, and it's displayed in the admin center for seven days.

## User experience

For work profile passcode reset, users get notified to activate their reset passcode. After their passcode is entered, the notification is dismissed.

Note

If the remote lock action fails, confirm that you have a device passcode policy assigned to the device. If the device doesn't have a device passcode assigned, the remote lock action doesn't succeed.

## Reference links

- Microsoft Graph API: [resetPasscode action](/en-us/graph/api/intune-devices-manageddevice-resetpasscode)