---
layout: Conceptual
title: 'Device Action: Rotate Recovery Lock Passcode - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-recovery-lock-passcode
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
description: Learn how to rotate the macOS Recovery Lock passcode with Microsoft Intune.
ms.date: 2026-03-09T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9b27e4c7-27fb-0ba0-4834-d2257637d0a9
document_version_independent_id: 9b27e4c7-27fb-0ba0-4834-d2257637d0a9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/rotate-recovery-lock-passcode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/rotate-recovery-lock-passcode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/rotate-recovery-lock-passcode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: bd982741-0878-8a29-df18-dc5161690116
---

# Device Action: Rotate Recovery Lock Passcode - Microsoft Intune | Microsoft Learn

Note

This feature is gradually rolling out and may not yet be available in your tenant. Full availability is expected by late April 2026.

Recovery Lock protects macOS devices by requiring a password to access recoveryOS. By using Intune, administrators can remotely rotate this passcode to keep access to the recovery environment secure and controlled.

When you use the **Rotate Recovery Lock Passcode** action, Intune creates a new passcode to replace the current one. The new passcode shows up in the admin center and is the only valid credential for accessing the device's recovery options.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - macOS in supervised mode, running macOS 11.5 or later on Apple silicon (Intel-based Macs aren't supported).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - Intune administrator
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks / Rotate macOS Recovery Lock password**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To run this action, the device must be configured with a policy setting that enables the Recovery Lock feature.
> 
> For more information, see [Create the Recovery Lock policy](../../device-configuration/settings-catalog/configure-recovery-lock-macos#create-the-recovery-lock-policy).

## How to rotate the macOS Recovery Lock passcode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Secure** &gt; **Rotate Recovery Lock Passcode**.
4. Select **Yes** to confirm the action. Intune generates a new Recovery Lock passcode.

Note

Confirming this action starts the passcode rotation process. The new Recovery Lock passcode is applied to the device the next time the device successfully checks in with Intune. If the device is offline or not checking in, the existing Recovery Lock passcode remains in effect until the device checks in.

To view the new passcode, select **Passwords and keys** &gt; **View Recovery Lock Passcode**.

## Reference links

- Microsoft Graph API: [managedDevice resource type](/en-us/graph/api/resources/intune-devices-manageddevice)