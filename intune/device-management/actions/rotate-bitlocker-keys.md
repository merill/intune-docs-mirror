---
layout: Conceptual
title: 'Device Action: BitLocker Key Rotation - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-bitlocker-keys
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
description: Learn how to rotate the BitLocker recovery key with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 45012c25-81e4-9be1-193f-584dfb78f417
document_version_independent_id: 45012c25-81e4-9be1-193f-584dfb78f417
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/rotate-bitlocker-keys.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/rotate-bitlocker-keys
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/rotate-bitlocker-keys.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 06677f0a-3e34-6bf7-b29a-428984f37cd9
---

# Device Action: BitLocker Key Rotation - Microsoft Intune | Microsoft Learn

The *BitLocker key rotation* action in Microsoft Intune lets IT admins remotely refresh the recovery key for the operating system drive on BitLocker-encrypted Windows devices. This helps reduce the risk of unauthorized access if a recovery key has been used or potentially exposed.

Key rotation is especially useful in environments where devices are frequently serviced, reassigned, or exposed to support scenarios. For example, if a helpdesk technician shares a recovery key during a support call, you can rotate the key from Intune to ensure it can't be reused.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Rotate BitLockerKeys**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to rotate the BitLocker key from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **BitLocker key rotation**.
4. Select **Yes** to confirm the action.

## Reference links

- Configuration service provider (CSP) used to initiate the action: [BitLocker CSP](/en-us/windows/client-management/mdm/bitlocker-csp#rotaterecoverypasswords)
- Microsoft Graph API: [rotateBitLockerKeys action](/en-us/graph/api/intune-devices-manageddevice-rotateBitLockerKeys)
- [BitLocker overview](/en-us/windows/security/operating-system-security/data-protection/bitlocker/)