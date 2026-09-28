---
layout: Conceptual
title: 'Device Action: Pause Config Refresh - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/pause-config-refresh
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
description: Learn how to temporarily pause policy enforcement on Windows 11 devices using Intune's Pause Config Refresh action to support troubleshooting and manual changes.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5caa52f5-3da0-7878-717e-d33d203a6aae
document_version_independent_id: 5caa52f5-3da0-7878-717e-d33d203a6aae
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/pause-config-refresh.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/pause-config-refresh
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/pause-config-refresh.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae6f8ad1-9a6a-1082-c241-eb2521f8d660
---

# Device Action: Pause Config Refresh - Microsoft Intune | Microsoft Learn

Use the *pause Config Refresh* action in Microsoft Intune to temporarily suspend automatic policy enforcement on Windows 11 devices. This action is helpful when you need to troubleshoot, perform maintenance, or apply manual changes that shouldn't be overwritten by Intune policies.

Config Refresh is a Windows feature that periodically reapplies policy settings to ensure devices stay compliant with your defined configurations. IT admins can configure the refresh cadence to run as frequently as every 30 minutes or as infrequently as once every 24 hours (1,440 minutes).

With the pause Config Refresh action, IT admins can suspend policy refresh for a specified duration—up to 1,440 minutes. After the pause period ends, Config Refresh resumes automatically.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Windows 11
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To use this action, make sure devices meet the following requirements:
> 
> - Config Refresh is enabled.
> 
> 
> To learn more, see [Config Refresh](/en-us/windows/security/book/operating-system-security-system-security#-config-refresh).

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Run Pause Configuration Refresh**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to pause Config Refresh from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Pause Config Refresh**.
4. Specify the number of minutes to pause Config Refresh in the **Time period to Pause Config Refresh**. The maximum is 1,440 minutes (24 hours).
5. Select **Pause**.

Note

If Config Refresh is paused and you want to resume, then select **Pause** again for 0 minutes to resume Config Refresh enforcement.

## Reference links

- Microsoft Graph API: [pauseConfigurationRefresh action](/en-us/graph/api/intune-devices-manageddevice-pauseconfigurationrefresh) in the Microsoft Graph API documentation.
- Configuration service provider (CSP) used to initiate the action: [DMClient CSP](/en-us/windows/client-management/mdm/dmclient-csp#deviceproviderprovideridconfigrefresh)