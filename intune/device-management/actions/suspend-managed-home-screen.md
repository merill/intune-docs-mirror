---
layout: Conceptual
title: 'Device Action: Suspend Managed Home Screen - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/suspend-managed-home-screen
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
description: Learn how to suspend the Managed Home Screen with Microsoft Intune.
ms.date: 2026-04-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b677575a-87f7-a764-5387-a8c52ec7ca24
document_version_independent_id: b677575a-87f7-a764-5387-a8c52ec7ca24
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/suspend-managed-home-screen.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/suspend-managed-home-screen
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/suspend-managed-home-screen.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 23773c04-e4aa-358c-bc69-e32aee6fd8bf
---

# Device Action: Suspend Managed Home Screen - Microsoft Intune | Microsoft Learn

The *suspend Managed Home Screen* device action in Intune temporarily disables the Managed Home Screen on a device. When the Managed Home Screen is suspended, the device will no longer enforce the Managed Home Screen policies, and the user will have access to the standard home screen and apps.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned Fully Managed (COBO)
> - Android Enterprise corporate-owned Dedicated (COSU)
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Temporarily Suspend Managed Home Screen**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To run this action, the **Alarms & Reminders** permission must be granted to the Managed Home Screen.
> 
> For more information, see [Configure permissions for the Managed Home Screen (MHS) on Android Enterprise devices using Microsoft Intune](../../device-configuration/templates/configure-managed-home-screen-permissions-android).

## How to suspend the managed home screen from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remote actions** &gt; **Suspend Managed Home Screen**.

## User experience

Once the Managed Home Screen is suspended, the device will no longer enforce the Managed Home Screen policies, and the user will have access to the standard home screen and apps.

## Reference links

- Microsoft Graph API: [managedDevice resource type](/en-us/graph/api/resources/intune-devices-manageddevice)
- Microsoft Graph API: [suspendManagedHomeScreen action](/en-us/graph/api/intune-devices-manageddevice-suspendmanagedhomescreen)