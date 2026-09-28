---
layout: Conceptual
title: 'Device Action: Restart - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/restart
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
description: Learn how to restart managed devices with Microsoft Intune.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: c5fbc3ee-cfe5-494a-b441-d95cbed3128c
locale: en-us
document_id: 5f40495e-c7dd-49cd-9b6e-771ef8f0aa7c
document_version_independent_id: 5f40495e-c7dd-49cd-9b6e-771ef8f0aa7c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/restart.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/restart
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/restart.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b4571d88-8115-aa34-d8d9-721dbe1f45d7
---

# Device Action: Restart - Microsoft Intune | Microsoft Learn

The *restart* action triggers a restart (usually begins within 5 minutes) and might not show a warning to the signed-in user.

Important

The restart depends on the device receiving a push notification. If the device is offline or push notifications are blocked, the restart is delayed until connectivity resumes.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned Dedicated (COSU)
> - Android Enterprise corporate-owned Fully Managed (COBO)
> - Android Open Source Project (AOSP)
> - ChromeOS (kiosk mode or managed guest session)
> - iOS/iPadOS in [Supervised Mode](/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - macOS
> - tvOS 10.2+ in [Supervised Mode](/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - Windows
> 

::: zone pivot="chromeos"

Note

Restart is only available for kiosk devices and managed guest session devices. The restart fails on any other type of device. For more information, see [Kiosk apps, managed guest sessions, and smart cards](https://support.google.com/chrome/a/topic/6128720?) (opens Google Chrome Enterprise Help).

::: zone-end

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Reboot now**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to restart a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Restart** &gt; **Yes**.

::: zone pivot="windows,ios"

## User experience

::: zone-end

::: zone pivot="ios"

A passcode-locked device can't reconnect to Wi-Fi until the user unlocks it. Apple encrypts saved Wi-Fi credentials until unlock. Until then, Intune can't communicate with the device.

::: zone-end

::: zone pivot="windows"

When the 5‑minute restart timer starts, Windows attempts to show the notification: *Your device administrator has scheduled a reboot.* Delivering the restart command requires Windows Notification Services (WNS).

For more information about WNS, see [Network endpoint requirements](../../fundamentals/endpoints#windows-push-notification-services-wns-dependencies).

::: zone-end

## Reference links

::: zone pivot="windows"

- Configuration service provider (CSP) used to initiate the action: [Reboot CSP](/en-us/windows/client-management/mdm/reboot-csp)

::: zone-end

- Microsoft Graph API: [rebootNow action](/en-us/graph/api/intune-devices-manageddevice-rebootnow)