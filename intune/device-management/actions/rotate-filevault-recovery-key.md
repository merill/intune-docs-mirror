---
layout: Conceptual
title: 'Device Action: Rotate FileVault Recovery Key - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-filevault-recovery-key
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
description: Learn how to rotate the FileVault recovery key with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: a0e2f9d8-a6f7-60a4-78d8-a1ff6b62da04
document_version_independent_id: a0e2f9d8-a6f7-60a4-78d8-a1ff6b62da04
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/rotate-filevault-recovery-key.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/rotate-filevault-recovery-key
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/rotate-filevault-recovery-key.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 49105b35-6236-e036-0c10-41bf2643496f
---

# Device Action: Rotate FileVault Recovery Key - Microsoft Intune | Microsoft Learn

The *rotate FileVault recovery key* action in Microsoft Intune allows IT admins to manually generate a new personal recovery key for a macOS device encrypted with FileVault.

This action is useful when the current key is lost, potentially exposed, or needs to be refreshed for compliance or support reasons.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - macOS (corporate-owned)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To use this action, make sure devices meet the following requirements:
> 
> - Are encrypted with FileVault using an Intune disk encryption policy.
> - Have the FileVault recovery key escrowed to Intune.
> 
> 
> For more information, see Use [FileVault disk encryption for macOS with Intune](../../device-configuration/endpoint-security/encrypt-filevault-macos).

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Rotate filevault key**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to rotate the FileVault recovery key from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Rotate FileVault recovery key**.
4. Select **Yes** to confirm the action.

## Reference links

- Microsoft Graph API: [rotateFileVaultKey action](/en-us/graph/api/intune-devices-manageddevice-rotateFileVaultKey)