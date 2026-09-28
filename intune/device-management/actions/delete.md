---
layout: Conceptual
title: 'Device Action: Delete - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/delete
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
description: Learn how to delete devices with Microsoft Intune.
ms.date: 2026-08-06T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 51e33912-415a-402f-8201-8acebf3e4991
locale: en-us
document_id: 28138cbf-cb45-bcaa-386a-47f046c6f037
document_version_independent_id: 28138cbf-cb45-bcaa-386a-47f046c6f037
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/delete.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/delete
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/delete.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b14c3847-e805-3d8e-0ee8-1d4c7aa382a4
---

# Device Action: Delete - Microsoft Intune | Microsoft Learn

Use the *delete* action in Intune to permanently remove devices that are no longer needed, being repurposed, or missing. This action helps cleanup your device inventory and ensures that unmanaged or obsolete devices no longer appear in the admin center.

Important

A tenant can submit up to 1,000 Delete actions per day. This tenant-wide limit is cumulative across individual device actions, bulk device actions, and Microsoft Graph API requests. The Delete limit applies to Delete requests even when deleting a device triggers a Retire or Wipe command. To request a limit change, [contact Microsoft support](../../fundamentals/it-pro-support/get-support-admin-center). For all device action limits, see [Daily tenant limits](./#daily-tenant-limits).

### Delete action behavior by platform

When you use the **Delete** action in Intune, the command that triggers depends on the device platform and, for Android, the enrollment type.

- For **Apple mobile**, **macOS**, and **Windows** devices, the Delete action always triggers a **Retire** command.
- For **Android** devices, the Delete action triggers either a **Retire** or **Wipe** command depending on the enrollment type.

| Platform | Enrollment Type | Action Triggered |
| --- | --- | --- |
| Windows | Any | [Retire devices](retire) |
| Apple mobile | Any | [Retire devices](retire) |
| macOS | Any | [Retire devices](retire) |
| Android | Device administrator | [Retire devices](retire) |
| Android | Personally-owned work profile (BYOD) | [Retire devices](retire) |
| Android | Corporate-owned Fully managed (COBO) | [Wipe devices](wipe) |
| Android | Corporate-owned Dedicated (COSU) | [Wipe devices](wipe) |
| Android | Corporate-owned Work profile (COPE) | [Wipe devices](wipe) |
| Android | Open Source Project (AOSP) | [Wipe devices](wipe) |

::: zone pivot="windows"

## Before retiring or deleting a Microsoft Entra joined device

If you delete or retire the Intune object for a Microsoft Entra joined device that is protected by BitLocker, Intune triggers a sync that removes key protectors. This action suspends BitLocker on the OS volume as a safeguard to prevent unrecoverable encryption scenarios when the Entra object is deleted.

Before retiring a Microsoft Entra joined device, make sure to back up any critical data that might be lost during the process, such as:

- BitLocker recovery key
- Local administrator account credentials

::: zone-end

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - tvOS
> - visionOS
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Managed devices/Delete**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to delete a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Delete**. To confirm, select **Yes**.

Note

This action might be governed by an Intune access policy that requires Multiple Administrative Approval (MAA). If so, a second administrator must approve the action before it can proceed.

For more information, see [Use access policies to require multiple administrative approvals](../../fundamentals/role-based-access-control/multi-admin-approval).

## Remove a device from Microsoft Entra ID

After executing the action on a device from Intune, you might also want to remove its record from Microsoft Entra ID to fully disconnect it from your organization's identity infrastructure. This step helps ensure that the device no longer appears in your tenant, avoids potential confusion in device inventory, and prevents lingering access permissions or stale records that could affect compliance or reporting.

For more information about removing devices from Microsoft Entra ID, see [Manage stale devices in Microsoft Entra ID](/en-us/entra/identity/devices/manage-stale-devices).

::: zone pivot="ios,macos"

## Remove an Apple ADE device from Apple Business Manager

After executing the action on an Apple Automated Device Enrollment (ADE) device in Intune, you might also need to release the device from Apple Business Manager to fully remove it from organizational control.

Follow these steps:

1. Go to http://business.apple.com, navigate to the **Devices** section, and search for the device using its serial number.
2. Select the device, opent the **...** menu, and the select **Release from Organization**.
3. Confirm the action by checking **I understand this cannot be undone**, and then select **Continue**.

Note

In some cases, the iOS device must be restored with iTunes to apply this change. Please find further instructions from Apple [here](https://support.apple.com/guide/itunes/restore-to-factory-settings-itnsdb1fe305/windows).

::: zone-end

## Delete action status

After you issue a **Delete** action, the device is removed from Intune management and is immediately hidden from the admin center. In the [Device actions report](../reports/overview#device-actions-report), the Delete action is reported with an **Action Status** of **Completed**.

Note

For **MDM devices**, deleting a device immediately hides it from the admin center and initiates a **Retire**. A status of **Completed** on a delete action means the process is complete on the server side; it doesn't confirm that the client device finished the **Retire**.

## Reference links

- Microsoft Graph API: [delete action](/en-us/graph/api/intune-devices-manageddevice-cleanwindowsdevice)