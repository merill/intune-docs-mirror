---
layout: Conceptual
title: 'Device Action: Remove Passcode - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/remove-passcode
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
description: Microsoft Intune remove passcode action helps you unlock devices remotely when users forget their passcodes. Discover how to use this feature.
ms.date: 2026-04-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9827d978-91d8-d0ef-e820-cf5c05aa9c67
document_version_independent_id: 9827d978-91d8-d0ef-e820-cf5c05aa9c67
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/remove-passcode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/remove-passcode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/remove-passcode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: ec2b07eb-6ef3-74b5-22bf-c094053c3e04
---

# Device Action: Remove Passcode - Microsoft Intune | Microsoft Learn

By using the *remove passcode* action in Microsoft Intune, you can remotely remove a device passcode. This action helps users regain access to their devices without requiring a full device wipe. this action is especially useful when a user forgets their passcode or is locked out of their device.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - iOS/iPadOS
> - visionOS 1.1+
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

## How to remove a passcode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remove passcode**.

## User experience

After the passcode is removed, if there's a passcode policy set, the device prompts the user to set a new passcode in Settings.

Important

If the **Remove passcode** action fails, Intune might have stored the wrong unlock token. You need to **Wipe** the device to regain access.

## Reference links

- Microsoft Graph API: [resetPasscode action](/en-us/graph/api/intune-devices-manageddevice-resetpasscode)