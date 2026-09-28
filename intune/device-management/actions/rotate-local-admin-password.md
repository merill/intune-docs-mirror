---
layout: Conceptual
title: 'Device Action: Rotate local admin password - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-local-admin-password
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
zone_pivot_group_filename: device-management/actions/zone-pivot-groups.json
description: Learn how to rotate the local admin password on Windows and macOS devices with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 2fce401c-16eb-4314-8d26-844d8612f9c5
locale: en-us
document_id: dc34f6b6-77cd-65b0-4fe6-aa0d013f0588
document_version_independent_id: dc34f6b6-77cd-65b0-4fe6-aa0d013f0588
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/rotate-local-admin-password.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/rotate-local-admin-password
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/rotate-local-admin-password.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
platformId: 16b71b05-40e9-8dfc-49c2-2c21bb5c8014
---

# Device Action: Rotate local admin password - Microsoft Intune | Microsoft Learn

The *rotate local admin password* action in Microsoft Intune lets IT admins manually rotate the password of a device's local administrator account. This helps improve security by refreshing credentials outside the scheduled rotation defined by the Microsoft Local Administrator Password Solution (LAPS). It's especially useful when responding to potential compromise, conducting audits, or resetting access during support scenarios.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - macOS [enrolled via Automated Device Enrollment (ADE)](../../device-enrollment/apple/setup-automated-macos)
> - Windows (corporate-owned)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

::: zone pivot="windows"

> 
> To use this action, make sure devices meet the following requirements:
> 
> - Are Microsoft Entra joined or Hybrid Entra joined.
> - Have Windows LAPS configured and actively backing up the local admin password to Microsoft Entra ID.
> 
> 
> For more information, see [What is Windows LAPS?](/en-us/windows-server/identity/laps/laps-overview).

::: zone-end

::: zone pivot="macos"

> 
> To use this action, make sure devices meet the following requirements:
> 
> - The local admin account must be configured in the ADE profile before enrollment.
> 
> 
> For more information, see [Configure support for macOS ADE local account with LAPS](../../device-security/laps/setup-macos).

::: zone-end

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Rotate Local Admin Password**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to rotate the local admin password from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Rotate Local admin password**.

## Reference links

- Microsoft Graph API: [rotatelocaladminpassword action](/en-us/graph/api/intune-devices-manageddevice-rotatelocaladminpassword)

::: zone pivot="windows"

- Configuration service provider (CSP) used to initiate the action: [LAPS CSP](/en-us/windows/client-management/mdm/laps-csp)

::: zone-end

- [Manually rotate passwords with Windows LAPS](../../device-security/laps/deploy-policy#manually-rotate-passwords)