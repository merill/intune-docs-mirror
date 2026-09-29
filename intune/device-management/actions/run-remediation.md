---
layout: Conceptual
title: 'Device Action: Run Remediation - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/run-remediation
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
description: Learn how to initiate on demand remediations with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 8c11c4d7-51dd-d1fa-bc80-903cf2b3cca2
document_version_independent_id: 8c11c4d7-51dd-d1fa-bc80-903cf2b3cca2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/run-remediation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/run-remediation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/run-remediation.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 74f0a9ae-a32f-3ee7-b407-26437425f8fc
---

# Device Action: Run Remediation - Microsoft Intune | Microsoft Learn

The *run remediation* action in Microsoft Intune allows IT administrators to proactively detect and resolve support issues on managed devices. This action triggers a remediation script that checks for specific conditions and applies a fix if needed—without requiring user interaction.

Use this action to address common problems such as configuration drift, missing settings, or compliance gaps. It's especially useful for maintaining device health across large environments.

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
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Run Remediation**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to run a remediation from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Run remediation**.
4. In the **Run remediation** pane, select the Script package you want to run from the list.
5. To run the remediation, select **Run remediation**.

To learn more about remediations in Microsoft Intune—including what they are, along with prerequisites and licensing requirements—see [Use Remediations to detect and fix support issues](../tools/deploy-remediations).

## Reference links

- Microsoft Graph API: [initiateOnDemandProactiveRemediation action](/en-us/graph/api/intune-devices-manageddevice-initiateondemandproactiveremediation)