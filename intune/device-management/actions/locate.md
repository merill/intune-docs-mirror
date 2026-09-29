---
layout: Conceptual
title: 'Device Action: Locate Device - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/locate
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
description: Locate lost or stolen devices by using the locate device feature in Microsoft Intune. Get details on security and privacy information when using the locate device action.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: d4b2a9c3-d659-4922-8403-9b50d065fc07
locale: en-us
document_id: bd1b5009-5a47-7f8c-abed-c02ee343e256
document_version_independent_id: bd1b5009-5a47-7f8c-abed-c02ee343e256
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/locate.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/locate
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/locate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 7595ac72-05d4-9116-1785-7362698e780f
---

# Device Action: Locate Device - Microsoft Intune | Microsoft Learn

The *locate device* device action in Microsoft Intune enables IT administrators to pinpoint the physical location of managed devices when they are lost, stolen, or simply misplaced. This feature is especially valuable in organizations where devices are distributed across multiple sites or used by mobile users. By triggering the Locate device action from the Intune admin center, admins can view the device's location on a map, helping accelerate recovery, reduce downtime, and improve compliance.

Depending on the platform, Intune can also report the last known location if the device is offline, [play a sound to locate lost devices](play-lost-mode-sound), or [enable lost mode to display custom messages on devices](lost-mode).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated (COSU)
> - Android Enterprise corporate-owned fully managed (COBO)
> - Android Enterprise corporate-owned work profile (COPE)
> - iOS/iPadOS in [Supervised Mode](../../device-enrollment/apple/enable-supervised-mode)
> - Windows
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
> - Location services must be turned on.
> - Intune app is installed.
> 
> 
> **Fully Managed Devices**:
> 
> - The **Locate Device** feature must be explicitly enabled with a device restrictions profile.
> 
> 
> **Corporate-Owned Work Profile Devices**:
> 
> - The **Locate Device** feature must be explicitly enabled with a device restrictions profile.
> - Users must grant location permission to the Intune app. Go to: **Settings** &gt; **Apps** &gt; **Intune (Work tab)** &gt; **Permissions** &gt; **Location** &gt; **Allow all the time**.
> 
> 
> **Dedicated Devices**:
> 
> - The **Locate Device** feature is enabled by default, unless explicitly blocked with a device restriction profile.
> 

Note

When **Locate device** is allowed, users receive a one-time notification, *Intune can access your location*, indicating that Intune has the ability to use location permissions on the device.

For more information about device restrictions, see [Android template device settings list to restrict features using Intune](../../device-configuration/templates/ref-device-restrictions-android-enterprise).

::: zone-end

::: zone pivot="windows"

> 
> Before you can use the locate functionality, you must configure your devices to allow it.
> 
> 1. [Create a Settings catalog policy](../../device-configuration/settings-catalog/) for the Windows platform and use the following setting:
> 
> 
>     | Category | Setting name | Value |
>     | --- | --- | --- |
>     | **Privacy** | Let Apps Access Location | Force allow |
> 2. Assign the policy to a group that contains as members the devices that you want to configure.
> 

::: zone-end

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permissions **Remote tasks/Locate device**, **Remote tasks/Play sound to locate lost devices**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 
> 
> ::: zone pivot="android"
> 
> For Android devices, the action is available only if the admin can read the policies that configure device location.
> 
> The account must:
> 
> - Have the **Device configuration/Read** permission.
> - Have scope tag visibility to the device restriction or settings catalog policy that enables location for the device.
> 
> 
> ::: zone-end

## Locate a device

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.

::: zone pivot="windows"

1. At the top of the device overview pane, find the row of action icons. Select **Locate device**.

::: zone-end

::: zone pivot="ios,android"

1. At the top of the device overview pane, find the row of action icons. Select **Locate** &gt; **Locate device**.

::: zone-end

1. After the device is located, its location is shown in **Locate device**. You can select the location pin on the map to view a location address and coordinates.

::: zone pivot="android"

Note

Android Enterprise corporate-owned dedicated (COSU) that aren't currently online can display their last known location when the device last checked in within seven days.

::: zone-end

![Map view showing the located device position with address and coordinates in the Intune admin center](media/locate/locate-device.png)

::: zone pivot="android"

### Last known location

When you use the *Locate device* action for an Android Enterprise dedicated device that is offline and unable to respond with its current location, Intune attempts to display its last known location. This capability uses data submitted by the device when it checks in with Intune.

Intune collects information about the last known location of a device every eight hours or when the device checks in with Intune. Intune keeps this information for up to seven days. The last known location of a device that hasn't checked in with Intune for more than seven days can't be displayed.

**About initialization of last known location**:

To support the *last know location* capability for Android dedicated devices, each device receives an initial default entry for **Locate device** which shows a status of **Complete**. This status appears under *Device actions status* when you view the devices Overview page. This default status is a result of Intune initializing the capability by default, which doesn't mean a locate device action has run.

The date and time of this default status varies:

- Devices that are enrolled before the capability becomes available, reflect the day this capability was enabled for your tenant.
- Devices that you enroll after this capability is available, reflect the time of device enrollment.

Later, this default status updates to reflect the actual date and time that an admin runs the Locate device action for that device.

::: zone-end

## Security and privacy information

Intune is designed to respect user privacy while providing powerful device management capabilities. When using the Locate Device action, here's what you need to know about how location data is handled:

- Location data is only collected when you initiate the Locate Device action—never before.
- Once triggered, the device's latitude and longitude are retrieved via the Graph API.
- All location data is encrypted in transit and at rest, ensuring secure handling.
- Data is stored for 24 hours and automatically deleted. Manual deletion is not supported.
- The last known location might be retained for up to seven days before being removed.
- On iOS/iPadOS devices, you can enable [Lost Mode](lost-mode) to remotely lock the device and display a custom message on the lock screen—helpful for recovery.
- In Android fully managed and corporate-owned work profile scenarios, users receive a notification when the Locate Device action is used—if notifications are enabled on the device.

## Reference links

- Microsoft Graph API:
    - [locateDevice action](/en-us/graph/api/intune-devices-manageddevice-locatedevice)
    - [playLostModeSound action](/en-us/graph/api/intune-devices-manageddevice-playlostmodesound)