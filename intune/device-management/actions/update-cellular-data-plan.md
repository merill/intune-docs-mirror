---
layout: Conceptual
title: Manage eSIM plans in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/update-cellular-data-plan
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
description: Activate and remove eSIM cellular plans on supported Apple and Android Enterprise devices with Microsoft Intune device actions.
ms.date: 2026-09-16T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1023
zone_pivot_groups: 22f7442d-9384-49c8-abff-aaa058b30589
locale: en-us
document_id: 1e215766-6b9c-4e90-75d3-2eb05e7acdef
document_version_independent_id: 1e215766-6b9c-4e90-75d3-2eb05e7acdef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/update-cellular-data-plan.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/update-cellular-data-plan
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/update-cellular-data-plan.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 3f6b39c2-d304-e955-287c-2ccd4a92309d
---

# Manage eSIM plans in Microsoft Intune - Microsoft Intune | Microsoft Learn

The *update cellular data plan* action lets you remotely activate an eSIM cellular plan on supported iOS/iPadOS devices, making it easier to manage connectivity for users without physical SIM cards. You can also activate eSIMs on one or more supported Android Enterprise devices and remove an eSIM from a single supported Android Enterprise device.

## Prerequisites

::: zone pivot="ios"

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - iOS/iPadOS
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, at a minimum, use an account that has one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Update cellular data plan**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

::: zone-end

::: zone pivot="android"

Android Enterprise eSIM actions support corporate-owned devices only. Personally owned devices with a work profile (BYOD) aren't supported.

| Action | Corporate-owned fully managed (COBO) | Corporate-owned dedicated (COSU) | Corporate-owned work profile (COPE) |
| --- | --- | --- | --- |
| Activate an eSIM on one device | Android 15 or later | Android 15 or later | Android 15 or later |
| Activate eSIMs on multiple devices | Android 15 or later | Android 15 or later | Android 15 or later |
| Remove an eSIM from one device | Android 15 or later | Android 15 or later | Android 17 or later |

The devices must support eSIM. Get the activation code or activation server URL from your carrier before you activate an eSIM. For bulk activation, we recommend using Google's literal `$url$` format for the carrier activation server URL.

To remove an eSIM, its ICCID must be available in the [device hardware inventory](../inventory-and-status/device-details#hardware-device-details). Use the ICCID to identify the eSIM that you want to remove.

To use an eSIM device action, at a minimum, use an account that has one of the following roles:

- [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
- [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
- [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
    - **Remote tasks/Update cellular data plan** to activate one or more eSIMs
    - **Remote tasks/Remove eSIM** to remove an eSIM
    - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)

::: zone-end

::: zone pivot="ios"

## Update the cellular data plan from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Update cellular data plan**. ![Screenshot of the Intune admin center Update cellular data plan action with an activation server URL field](media/update-cellular-data-plan/update-cellular-data-plan.png)
4. Enter the activation server URL for your mobile carrier and select **Update cellular plan**.

::: zone-end

::: zone pivot="android"

## Activate an eSIM on one Android Enterprise device

The single-device action is available only in the new device view.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. Set **Preview new device view** to **On**, and then select a supported Android Enterprise device.
3. At the top of the device overview pane, select **Activate eSIM**.
4. Enter the carrier-provided activation code, and confirm the action.

Intune sends the activation request without first blocking it based on reported eSIM slot capacity. If Google can't complete the activation, Intune surfaces the error returned by Google.

## Activate eSIMs on multiple Android Enterprise devices

Use a bulk device action to activate eSIMs on up to 100 supported devices with the same carrier activation server URL.

Note

Bulk eSIM activation is available only in the updated bulk device actions experience. It isn't available in the legacy experience.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices) &gt; [**Bulk device actions**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_Devices/BulkActionWizardBlade).
2. On the **Basics** page, select **Android** for the operating system and **Activate eSIM** for the device action.
3. In **Enter carrier activation server URL**, enter the URL provided by your carrier. We recommend using Google's literal `$url$` format. Select **Next**.
4. On the **Devices** page, select up to 100 supported corporate-owned Android Enterprise devices. Select **Next**.
5. On the **Review + create** page, review the action, and then select **Create**.

## Remove an eSIM from one Android Enterprise device

Removal depends on the ICCID reported in device inventory, and the single-device action is available only in the new device view.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. Set **Preview new device view** to **On**, and then select a supported Android Enterprise device.
3. In the device inventory, find and copy the ICCID for the eSIM that you want to remove. If the ICCID isn't available in inventory, you can't submit the removal action.
4. At the top of the device overview pane, select **Remove eSIM**.
5. Enter the ICCID, and confirm the action.

::: zone-end

::: zone pivot="ios"

## User experience

When you select the **Update cellular data plan** action, the device receives a command to activate the eSIM cellular data plan. The user experience on the device is as follows:

- Cellular data starts working.
- The active cellular data plan is listed in the cellular section of the **Settings** app on the device.

For more information about devices that support eSIM, see the Apple support article [Using Dual SIM with an eSIM](https://support.apple.com/HT209044).

::: zone-end

::: zone pivot="android"

## User experience

When you activate an eSIM on a supported corporate-owned Android Enterprise device, the eSIM is downloaded and activated automatically. A bulk activation uses the same carrier activation server URL for all selected devices. When you remove an eSIM, the device removes the eSIM identified by the ICCID that you entered.

::: zone-end

## Reference links

- Microsoft Graph API: [activateDeviceEsim action](/en-us/graph/api/intune-devices-manageddevice-activateDeviceEsim)