---
layout: Conceptual
title: Enroll devices using a device enrollment manager account - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/setup-enrollment-manager
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Use the device enrollment manager account to enroll devices in Intune.
ms.date: 2025-06-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: 
locale: en-us
document_id: ea838bda-5684-3588-5680-e60d24eeb92e
document_version_independent_id: ea838bda-5684-3588-5680-e60d24eeb92e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/setup-enrollment-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/setup-enrollment-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/setup-enrollment-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 088fcfbe-fe94-0dd6-ab73-a94aca0c7dab
---

# Enroll devices using a device enrollment manager account - Microsoft Intune | Microsoft Learn

A device enrollment manager (DEM) is a nonadministrator user who can enroll devices in Intune. Device enrollment managers are useful to have when you need to enroll and prepare many devices for distribution. People signed in to a DEM account can enroll and manage up to 1,000 devices, while a standard nonadmin account can only enroll 15.

Tip

The following enrollment methods allow standard nonadmin accounts to enroll more than 15 devices:

- Co-management with Configuration Manager
- Automatic enrollment + group policy
- Windows Autopilot

If you're using these methods to enroll devices, you do not need to use a DEM account.

A DEM account requires an Intune user or device license, and an associated Microsoft Entra user. This article describes the limits and specifications of DEM accounts and how to manage permissions.

## Supported enrollment methods

A device enrollment manager can use the following methods to enroll devices in Intune:

- [Bulk enrollment using a provisioning package](windows/create-bulk-package)
- DEM-initiated via Company Portal enrollment
- DEM-initiated via Microsoft Entra join

Tip

To compare DEM best practices and capabilities alongside other Windows enrollment methods, see [Intune enrollment method capabilities for Windows devices](windows/guide).

## Requirements

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To manage device enrollment manager accounts, you must be assigned the [**Intune Administrator**](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) role.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

### Permissions

The Intune Administrator role can *update* and *read* device enrollment manager accounts.

| Permission | Description |
| --- | --- |
| Update | Create new device enrollment manager accounts, or delete device enrollment manager accounts. |
| Read | View the list of device enrollment manager accounts. |

## Add a device enrollment manager

Tip

Only use dedicated accounts that are not assigned to an individual user as Device enrollment manager accounts.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Device enrollment managers** tab.
4. Choose **Add**.
5. In the **User name** field, enter the user principal name of the user you're adding.
6. Select **Add**. The new device enrollment manager is added to the list of DEM users.

To remove someone as a device enrollment manager, select their name in the list and then choose **Delete**.

Tip

Do not delete accounts assigned as a Device enrollment manager if any devices were enrolled using the account. Doing so will lead to issues with these devices.

## Limitations

The device enrollment manager account can't be used with all features in Microsoft Intune and has some limitations when used with others. This section describes the limitations you could encounter while setting up devices from a DEM account.

### Android Enterprise

You can enroll up to 10 personally owned devices with work profiles.

The following types of Android Enterprise devices can't be set up via DEM:

- Corporate-owned devices with a work profile
- Fully managed devices

### Android open source project (AOSP)

AOSP doesn't support DEM accounts.

### App assignments

There are no users associated with a DEM-enrolled device, so apps can't be deployed as **Available**.

### Apple Automated Device Enrollment

DEM isn't compatible with Apple Automated Device Enrollment (ADE).

### Apple volume purchased apps

DEM-enrolled devices can install VPP apps if they have Apple VPP device licenses. You can't use apps purchased through Apple VPP with Apple VPP user licenses, because of per-user Apple ID requirements for app management.

### Certificates

You must use device-level certificates to manage Wi-Fi and email connections.

### Conditional Access

Conditional Access is only supported with DEM on devices running:

- Windows 10, version 1803 and later
- Windows 11

Note

DEM accounts on iOS/iPadOS and macOS do not support Microsoft Entra Join, Microsoft Entra registration, and Workplace Join.

### Device limit restrictions

DEM enrolls Windows devices in shared device mode, so device limit restrictions won't work on them. Instead, you can configure a hard limit for these devices in the Microsoft Entra admin center. For more information, see [Manage device identities](/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).

### Intune Company Portal

Only the local device appears in the Company Portal app or Company Portal website. Device users can't wipe DEM-enrolled devices from Company Portal. You have to sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) to wipe these devices.

### Microsoft Entra ID

Applying a Microsoft Entra maximum device limit of less than 1,000 to a DEM account prevents you from reaching the 1,000 device limit that the DEM account can enroll.

### Number of accounts

There's a limit of 150 DEM accounts in Microsoft Intune.

### VPN profiles

User-based VPN profiles don't work with DEM-enrolled devices.