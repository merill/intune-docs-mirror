---
layout: Conceptual
title: Device association lifecycle management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/device-association/lifecycle-management
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
description: Manage the Windows Autopilot device association lifecycle, including resetting devices, uploading updated device information, working with registered Windows Autopilot devices, stale records, and decommissioning.
ms.date: 2026-09-01T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ba1972b2-74e3-19b5-5d15-30bae8a826b3
document_version_independent_id: ba1972b2-74e3-19b5-5d15-30bae8a826b3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/device-association/lifecycle-management.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/device-association/lifecycle-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/device-association/lifecycle-management.md
platformId: a966793a-4fe1-523a-0326-17ff5e2bc276
---

# Device association lifecycle management | Microsoft Learn

This article describes how to manage common events throughout the device association lifecycle.

## Resetting an associated device

The tenant affinity created by device association is stored in the device's UEFI firmware, so it persists across a device reset, a Windows reinstall, and enrollment removal. Resetting the device alone doesn't remove the association.

To fully remove the association, clear the tenant affinity on the device itself by clearing the association information—for example, by running a PowerShell script to remove association. This requires physical access to the device. For instructions, see [Remove association from a device](remove-association).

Important

Physical access to the device is required to clear the device's tenant affinity. The person with physical access to a device is treated as its owner from an association security perspective.

## Removing association locally on a device

If the association information is cleared locally on the device—for example, by running a PowerShell script to remove association—the behavior depends on whether the device is still enrolled with its mobile device management (MDM) provider:

- **The device is still enrolled with its MDM provider.** The MDM provider attempts to re-associate the device on its next check-in.
- **The device is no longer enrolled with its MDM provider.** The MDM provider doesn't know that the association information was removed, so the device's association record remains stale.

## Uploading a new CSV file for an already pre-associated device

If a device already has a pre-association record in your tenant and you upload a new CSV for the same device:

- **If the device's hardware identity hasn't changed**, the existing pre-association record is updated. For example, if you're assigning a different device preparation policy, the record is updated in place.
- **If the device's hardware identity has changed**—which happens when someone clears UEFI via PowerShell script, resets the BIOS/UEFI settings, or toggles Secure Boot—the service can no longer match the new submission to the original device. In this case, a new pre-association record is created and the original record becomes stale. The new record is associated during OOBE as normal.

## Pre-associating a device that is registered for Windows Autopilot

If a device is already registered for Windows Autopilot, you can still pre-associate it. When the device goes through OOBE, the device association takes precedence. The device is enrolled using the device preparation policy. For guidance on exporting device information from an existing device, see [How do I get the DeviceLink CSV for a device that's already set up?](faq#how-do-i-get-the-devicelink-csv-for-a-device-thats-already-set-up).

## Managing stale records

A pre-association record becomes stale when:

- A new pre-association record is created for the same device because the hardware identity changed.
- The device was pre-associated and then associated with a different tenant.

Note

Stale pre-associated device records are automatically deleted after 360 days. No manual cleanup is required.

## Decommissioning a device

You only need to remove association when the device is permanently leaving your tenant. To do so, follow the steps in [Remove association from a device](remove-association).