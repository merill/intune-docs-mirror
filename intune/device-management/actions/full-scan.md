---
layout: Conceptual
title: 'Device Action: Full Scan - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/full-scan
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
description: Learn how to initiate on demand Microsoft Defender full scan with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 40a64814-5e85-b0f9-7519-9d2e56f4e13f
document_version_independent_id: 40a64814-5e85-b0f9-7519-9d2e56f4e13f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/full-scan.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/full-scan
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/full-scan.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e8dabd11-cf2a-1ef7-9b2f-f5bd488a2f57
---

# Device Action: Full Scan - Microsoft Intune | Microsoft Learn

The *full scan* action in Intune lets IT admins trigger a comprehensive malware scan on managed Windows devices using Microsoft Defender Antivirus. It checks all files and running processes, helping detect threats missed by quick scans.

This action is ideal when a device is suspected of compromise or when validating security baselines. Instead of waiting for scheduled scans or relying on user action, admins can launch a full scan directly from the Intune admin center.

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
>     - The permission **Remote tasks/Windows defender**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to initiate a full scan from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Microsoft Defender** &gt; **Run full malware scan**.

## Reference links

- Microsoft Graph API: [windowsDefenderScan action](/en-us/graph/api/intune-devices-manageddevice-windowsdefenderscan)
- Configuration service provider (CSP) used to initiate the action: [Defender CSP](/en-us/windows/client-management/mdm/defender-csp)