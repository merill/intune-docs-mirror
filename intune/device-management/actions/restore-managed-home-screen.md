---
layout: Conceptual
title: 'Device Action: Restore Managed Home Screen - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/restore-managed-home-screen
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
description: Learn how to restore the Managed Home Screen with Microsoft Intune.
ms.date: 2026-04-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 44ec81b9-0caf-cd42-2615-6041816069dc
document_version_independent_id: 44ec81b9-0caf-cd42-2615-6041816069dc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/restore-managed-home-screen.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/restore-managed-home-screen
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/restore-managed-home-screen.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 25979186-1991-9eed-bfb7-0913d68042de
---

# Device Action: Restore Managed Home Screen - Microsoft Intune | Microsoft Learn

The *restore Managed Home Screen* device action in Intune re-enables the Managed Home Screen on a device that was previously suspended. When the Managed Home Screen is restored, the device will enforce the Managed Home Screen policies again, restricting access to only the apps and settings defined by those policies.

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
>     - The permission **Remote tasks/Restore Managed Home Screen**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To run this action, the **Alarms & Reminders** permission must be granted to the Managed Home Screen.
> 
> For more information, see [Configure permissions for the Managed Home Screen (MHS) on Android Enterprise devices using Microsoft Intune](../../device-configuration/templates/configure-managed-home-screen-permissions-android).

## How to restore the managed home screen from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Restore Managed Home Screen**.

## User experience

Once the Managed Home Screen is restored, the device will enforce the Managed Home Screen policies again, and the user will have access to the Managed Home Screen and apps.

## Reference links

- Microsoft Graph API: [managedDevice resource type](/en-us/graph/api/resources/intune-devices-manageddevice)
- Microsoft Graph API: [restoreManagedHomeScreen action](/en-us/graph/api/intune-devices-manageddevice-restoremanagedhomescreen)