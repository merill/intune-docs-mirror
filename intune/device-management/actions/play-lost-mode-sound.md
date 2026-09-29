---
layout: Conceptual
title: 'Device Action: Play Lost Mode Sound - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/play-lost-mode-sound
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
description: Learn how to use the Play lost device sound action in Microsoft Intune to trigger an audible alert on a lost, stolen, or misplaced device—helping users locate it quickly and securely.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 22f7442d-9384-49c8-abff-aaa058b30589
locale: en-us
document_id: df54e0b3-a2e0-8d60-94e8-225e00da3f78
document_version_independent_id: df54e0b3-a2e0-8d60-94e8-225e00da3f78
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/play-lost-mode-sound.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/play-lost-mode-sound
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/play-lost-mode-sound.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 15776cde-8626-f805-cda8-63424c2a3a37
---

# Device Action: Play Lost Mode Sound - Microsoft Intune | Microsoft Learn

Microsoft Intune provides platform-specific device actions to help locate a lost or misplaced device by triggering an audible alert—even if the device is locked or silenced.

- On iOS/iPadOS, use the *play Lost Mode sound* action. This action is available when the device is in [Lost Mode](lost-mode) and supervised.
- On Android Enterprise devices, use the *Play lost device sound* action. This action is supported for corporate-owned devices enrolled with Android Enterprise.

These device actions are especially useful in environments where devices are shared or frequently moved—such as classrooms, labs, or enterprise workspaces. Playing a sound helps users or administrators locate the device quickly and securely, supporting recovery efforts when a device is lost.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated (COSU)
> - Android Enterprise corporate-owned fully managed (COBO)
> - Android Enterprise corporate-owned work profile (COPE)
> - iOS/iPadOS in [Supervised Mode](../../device-enrollment/apple/enable-supervised-mode)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

::: zone pivot="ios"

> 
> To use this action, make sure devices meet the following requirements:
> 
> - Enable [Lost Mode](lost-mode)
> 

::: zone-end

::: zone pivot="android"

> 
> To use this action, make sure devices meet the following requirements:
> 
> - Intune app is installed.
> 

::: zone-end

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Play sound to locate lost devices**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to play lost mode sound from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.

::: zone pivot="ios"

1. At the top of the device overview pane, locate the row of action icons. Select **Locate** &gt; **Play Lost Mode sound (supervised only)**.

::: zone-end

::: zone pivot="android"

1. At the top of the device overview pane, locate the row of action icons. Select **Locate** &gt; **Play lost device sound**.

::: zone-end

1. Select the duration for the sound to play on the device, and then select **Yes**.

## User experience

::: zone pivot="ios"

The sound plays until the user disables the sound or the duration you set expires.

::: zone-end

::: zone pivot="android"

If system notifications are enabled, the device displays a notification with a **Stop Sound** button. The alert plays for the configured duration or until a user on the device manually stops it using the notification.

Notification behavior might vary based on system settings. To configure system notifications, see [Android Enterprise device settings to allow or restrict features using Intune](../../device-configuration/templates/ref-device-restrictions-android-enterprise).

::: zone-end

## Reference links

- Microsoft Graph API: [playLostModeSound action](/en-us/graph/api/intune-devices-manageddevice-playlostmodesound)