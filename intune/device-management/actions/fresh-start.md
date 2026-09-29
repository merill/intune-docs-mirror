---
layout: Conceptual
title: 'Device Action: Fresh Start - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/fresh-start
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
description: Learn how to use Fresh Start to remove or uninstall apps with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 6f269ea5-815b-1d70-35d9-5debad1ff28d
document_version_independent_id: 6f269ea5-815b-1d70-35d9-5debad1ff28d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/fresh-start.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/fresh-start
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/fresh-start.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: dded816d-01b2-b098-8d1e-851c0f8cc235
---

# Device Action: Fresh Start - Microsoft Intune | Microsoft Learn

The *Fresh Start* action removes apps from managed Windows devices, helping you remove preinstalled (OEM) apps that typically ship with a new PC.

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
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Clean PC**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to run Fresh Start from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remove data** &gt; **Fresh Start**.
4. Select **Retain user data on this device** to:

    - Keep the device Microsoft Entra joined.
    - Automatically re-enroll the device in mobile device management when a Microsoft Entra ID-enabled user signs in.
    - Preserve the contents of the user's Home folder, while removing apps and settings.

    Important

    If you don't retain user data, the device is restored to the default out-of-box experience (OOBE) completed state retaining the built-in administrator account. BYOD devices are removed from Microsoft Entra ID and mobile device management.
5. Select **OK**.

## Reference links

- Configuration service provider (CSP) used to initiate the action: [CleanPC CSP](/en-us/windows/client-management/mdm/cleanpc-csp)
- Microsoft Graph API: [cleanWindowsDevice action](/en-us/graph/api/intune-devices-manageddevice-cleanwindowsdevice)