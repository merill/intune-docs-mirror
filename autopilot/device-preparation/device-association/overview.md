---
layout: Conceptual
title: Overview of Windows Autopilot device association | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/device-association/overview
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
description: Device association binds a Windows device to your organization before enrollment by stamping tenant affinity into the device's UEFI, enabling a streamlined OOBE, device naming, device-based policy targeting, and stronger onboarding security.
ms.date: 2026-08-25T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: 8c11a0df-5d71-7894-fa2c-1dd83580c2d6
document_version_independent_id: 8c11a0df-5d71-7894-fa2c-1dd83580c2d6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/device-association/overview.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/device-association/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/device-association/overview.md
platformId: 91789dfd-f8ed-44e7-40eb-9f73bf25bc56
---

# Overview of Windows Autopilot device association | Microsoft Learn

Device association is a feature of Windows Autopilot device preparation that binds a Windows device to your organization *before* the device enrolls with a mobile device management (MDM) provider, such as Microsoft Intune. It establishes a verifiable link between a physical device and your tenant by writing a tenant affinity marker into the device's UEFI firmware, making the device recognizable and authenticatable by the MDM provider before enrollment begins. By establishing this trusted relationship early in the provisioning process, device association unlocks a streamlined out-of-box experience (OOBE) and strengthens the security of onboarding.

## Benefits

Device association provides the following benefits:

- **Streamlined out-of-box experience (OOBE)** - Because the device is recognized as an organizational device before enrollment, OOBE can present a simpler, more consistent set of pages to the end user. You can preconfigure settings such as language, keyboard layout, and skipping the license and privacy pages.
- **Device naming before enrollment** - Apply a device name using a template before the device enrolls, so the device carries the correct name from the start of its lifecycle.
- **Device-based policy targeting** - Target device preparation policies directly to devices instead of relying solely on user group assignments, so the correct policy is applied regardless of which user signs in.
- **Automatic corporate marking** - Associated devices are automatically marked as corporate-owned, so they aren't blocked by [personal device enrollment restrictions](/en-us/intune/device-enrollment/restrictions#personally-owned-devices)—no separate [corporate identifier](/en-us/intune/device-enrollment/add-corporate-identifiers#add-windows-corporate-identifiers) upload needed.
- **Stronger onboarding security** - Device identity is verified before enrollment through hardware-based attestation and TPM-backed cryptographic validation, helping ensure that only trusted devices can access organizational resources.

## How device association works

Device association uses the device's TPM-backed identity to establish a trusted association between the device and your tenant. It involves three lifecycle operations:

| Operation | Performed by | Description |
| --- | --- | --- |
| **Pre-associate** | Administrator in Intune | Stores the intent to create a TPM-backed association between the device and your tenant in a central service before the association is written to UEFI. |
| **Associate** | Automatic—triggered by the technician after pre-associating, or when the device connects to a network in OOBE | Verifies that the device presents the expected TPM-backed identity, and then writes a marker containing tenant affinity information to the device's UEFI. The marker is used to attest the device's affinity at enrollment. |
| **Remove association** | Admin, OEM vendor, or partner, by running a PowerShell script on the device | Deletes the UEFI marker used to verify the device's association, clearing the trusted tenant affiliation from UEFI storage. |

The high-level workflow is:

1. **Create a device preparation policy** with the deployment and OOBE experience settings you want to apply.
2. **Export device information** from the device during OOBE.
3. **Pre-associate the device** in Intune by uploading the exported CSV, and optionally assign a device preparation policy.
4. **Associate the device.** Association happens automatically when the device connects to a network in OOBE. A technician can also trigger it manually in OOBE, immediately after pre-associating. Associating the device stamps the UEFI marker.
5. **Enroll the device.** It receives the device-targeted policy, is marked as corporate-owned, and has the configured OOBE customizations applied.
6. **Remove association** when the device is permanently leaving your tenant, such as when you decommission it.

## Key capabilities

### Device-targeted policy assignment

Assign a device preparation policy directly to a pre-associated device, so the correct policy applies regardless of which user signs in. One user can enroll multiple devices, each with a different policy.

### OOBE customization

Device association enables the following settings in the device preparation user-driven policy, applied before enrollment:

- **Language (Region)** - Select the language to use for the device.
- **Automatically configure keyboard** - When a language is selected, skip the keyboard selection page.

    Note

    When the device uses a Wi-Fi network connection during OOBE, the language and keyboard selection screens aren't hidden.
- **Hide Microsoft Software License Terms** - Skip the End-User License Agreement (EULA) page during OOBE.
- **Hide privacy settings** - Skip the privacy settings page during OOBE. When privacy settings are hidden, location services are disabled by default.
- **Hide change account options** - Prevent change account options from appearing on the company sign-in and domain error pages. This setting requires company branding to be configured in Microsoft Entra ID.
- **Apply device name template** - Name the device during enrollment by using a template. Names can be up to 63 characters long and can contain letters, numbers, and hyphens, but can't contain only numbers. Use `%SERIAL%` to include the device serial number or `%RAND:x%` to include a random numeric string, where `x` is the number of digits.

Note

On Windows Professional editions, the **Personal account / Work and school account** page is hidden by default for all associated devices.

### Device monitoring

Monitor the status of pre-associated and associated devices from the **Device association** blade in Intune under **Devices** &gt; **Enrollment** &gt; **Device association** &gt; **Devices**. The blade shows each device's association state and assigned device preparation policy, and lets you filter by state, policy, manufacturer, and model.

## Limitations

The following limitations apply in the current release:

- Removing association from Intune isn't supported. To remove an association, clear the association information on the device instead. For more information, see [Remove association from a device](remove-association).
- Device association doesn't apply to Windows 365 devices because they're already marked as trusted corporate devices.