---
layout: Conceptual
title: DFCI Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/dfci-management
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: With Windows Autopilot Deployment and Intune, Unified Extensible Firmware Interface (UEFI) settings can be managed after the device is enrolled. UEFI settings can be managed by using the Device Firmware Configuration Interface (DFCI).
ms.date: 2025-03-25T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: article
locale: en-us
document_id: 159464c0-60b1-25f8-f9c7-b3fae3d27eed
document_version_independent_id: 159464c0-60b1-25f8-f9c7-b3fae3d27eed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/dfci-management.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: dfci-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/dfci-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7399d4a7-f8bb-5bcf-0500-ee60911b1e85
---

# DFCI Management | Microsoft Learn

With Windows Autopilot Deployment and Intune, Unified Extensible Firmware Interface (UEFI) settings can be managed after the device is enrolled. UEFI settings can be managed by using the Device Firmware Configuration Interface (DFCI). DFCI [enables Windows to pass management commands](/en-us/windows/client-management/mdm/uefi-csp) from Intune to UEFI for Windows Autopilot deployed devices. This capability allows limiting end user's control over BIOS settings. For example, the boot options can be locked down to prevent users from booting up another OS, such as one that doesn't have the same security features.

If a user reinstalls a previous Windows version, installs a separate OS, or formats the hard drive, they can't override DFCI management. This feature can also prevent malware from communicating with OS processes, including elevated OS processes. DFCI's trust chain uses public key cryptography, and doesn't depend on local UEFI password security. This layer of security blocks local users from accessing managed settings from the device's UEFI menus.

For an overview of DFCI benefits, scenarios, and requirements, see [Device Firmware Configuration Interface (DFCI) Introduction](https://microsoft.github.io/mu/dyn/mu_feature_dfci/DfciPkg/Docs/Dfci_Feature/).

Important

A device automatically enrolls in DFCI management during Windows Autopilot provisioning when the following actions occur:

- The OEM enables the device for DFCI.
- The device is registered for Windows Autopilot via the OEM or a Cloud Solution Partner (CSP) in Partner Center.

Enrollment in DFCI management triggers an additional reboot during the out-of-box experience (OOBE).

## DFCI management lifecycle

The DFCI management lifecycle includes the following processes:

- UEFI integration.
- Device registration.
- Profile creation.
- Enrollment.
- Management.
- Retirement.
- Recovery.

See the following figure:

![Screenshot that shows Device Firmware Configuration Interface (DFCI) Management workflow](images/dfci.png)

## Requirements

- A currently supported version of Windows and a supported UEFI is required.
- The device manufacturer must have DFCI added to their UEFI firmware in the manufacturing process, or as a firmware update that can be installed. Work with the device vendors to determine the manufacturers that support DFCI, or the firmware version needed to use DFCI.
- The device must be managed with Microsoft Intune. For more information, see [Enroll Windows devices in Intune using Windows Autopilot](enrollment-autopilot).
- The device must be registered for Windows Autopilot by a [Microsoft Cloud Solution Provider (CSP) partner](https://partner.microsoft.com/membership/cloud-solution-provider), or registered directly by the OEM. For Surface devices, Microsoft registration support is available at [Microsoft Devices Windows Autopilot Support](https://support.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f).

Important

Devices manually registered for Windows Autopilot (such as by [importing from a CSV file](enrollment-autopilot#add-devices)) aren't allowed to use DFCI. By design, DFCI management requires external attestation of the device's commercial acquisition through an OEM or a Microsoft CSP partner registration to Windows Autopilot. When the device is registered, its serial number is displayed in the list of Windows Autopilot devices.

## Managing DFCI profile with Windows Autopilot

There are four basic steps in managing DFCI profile with Windows Autopilot:

1. Create a Windows Autopilot Profile
2. Create an Enrollment status page profile
3. Create a DFCI profile
4. Assign the profiles

See [Create the profiles](/en-us/intune/device-configuration/templates/configure-dfci-windows#create-the-profiles) and [Assign the profiles, and reboot](/en-us/intune/device-configuration/templates/configure-dfci-windows#assign-the-profiles-and-reboot) for details.

The existing [DFCI settings](/en-us/intune/device-configuration/templates/configure-dfci-windows#update-existing-dfci-settings) can also be changed on devices that are in use. In the existing DFCI profile, change the settings and save the changes. Since the profile is already assigned, the new DFCI settings take effect when next time the device syncs or the device reboots.

To identify whether a device is DFCI ready, the following Intune Graph API call can be used:

`managedDevice/deviceFirmwareConfigurationInterfaceManaged`

For more information, see [Intune devices and apps API overview](/en-us/graph/intune-concept-overview) and [Working with Intune in Microsoft Graph](/en-us/graph/api/resources/intune-graph-overview).

## OEMs that support DFCI

- Acer.
- Asus.
- Dynabook.
- Fujitsu.
- [Microsoft Surface](/en-us/surface/surface-manage-dfci-guide).
- Panasonic.
- VAIO.
- Samsung.
- NEC.

Other OEMs are pending.

## Known issues

### DFCI enrollment fails for Professional editions of Windows 11, version 24H2

Date added: *October 9, 2024* Date updated: *February 11, 2025*

DFCI can't currently be configured during the out-of-box experience (OOBE) on devices with Professional editions of Windows 11, version 24H2

For devices that have already been provisioned and have Professional editions of Windows 11, version 24H2, install [KB5046740](https://support.microsoft.com/topic/november-21-2024-kb5046740-os-build-26100-2454-preview-2040f716-b719-482a-8aff-f7f02c79b147) or later to enroll in DFCI. Devices with Professional editions of Windows 11, version 24H2 that have KB5046740 or later installed are automatically enrolled in DFCI after a reboot.

If DFCI needs to be configured during OOBE provisioning on 24H2 devices, follow these steps:

1. During OOBE onboarding, ensure the device is upgraded to the Enterprise edition of Windows 11, version 24H2.
2. After upgrading to the Enterprise edition of Windows 11, version 24H2, sync the device.
3. Once the device is synced, reboot it to get it enrolled in DFCI.