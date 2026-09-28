---
layout: Conceptual
title: Windows Autopilot device association FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/device-association/faq
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
description: Frequently asked questions about Windows Autopilot device association, including exported CSV content, corporate identifiers, OEM support, and virtual machines.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: faq
locale: en-us
document_id: 7d2427db-12cb-c6a1-a95c-19e5f3672f71
document_version_independent_id: 7d2427db-12cb-c6a1-a95c-19e5f3672f71
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/device-association/faq.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/device-association/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/device-association/faq.md
platformId: f45aca64-8343-3972-7b92-e4d914afa488
---

# Windows Autopilot device association FAQ | Microsoft Learn

This article answers common questions about Windows Autopilot device association.

## General

### Why did the CSV content for association change?

If you export the device information CSV multiple times, the exported information may look different because the DeviceLink contains metadata timestamps. This behavior is expected, and the device's hardware identity doesn't change.

A changed CSV doesn't invalidate an existing pre-association on its own. A pre-association is invalidated only when the device's hardware identity changes—for example, after you run a PowerShell script to remove association, reset the BIOS/UEFI settings, or change the Secure Boot configuration. After the identity is cleared on the device, you can export a new DeviceLink CSV and upload it to pre-associate the device again.

### How do I get the DeviceLink CSV for a device that's already set up?

For existing devices that are past the out-of-box experience (OOBE), you can export the device information from the device's Autopilot diagnostic logs instead of using the OOBE Autopilot menu. On the device, go to **Settings** &gt; **Accounts** &gt; **Access work or school**, select **Export your management logs** under **Related settings**, and then retrieve the DeviceLink CSV from the exported diagnostics. You can also run `MdmDiagnosticsTool.exe -area Autopilot -cab <path>` from an elevated command prompt, or collect the diagnostics remotely from the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) (**Devices** &gt; select the device &gt; **Collect diagnostics**). Upload the exported CSV in Intune to pre-associate the device. For more information, see [Associate devices](../tutorial/user-driven/entra-join-device-association).

### Do I need to upload corporate identifiers if my devices are pre-associated?

No. Pre-associated and associated devices are automatically marked as corporate-owned, so you don't need to upload corporate identifiers for them—even if you use enrollment restrictions to block personal device enrollments. Corporate identifiers and device association are two alternative ways to make sure only trusted devices are onboarded; you don't need both.

### Can an OEM, reseller, or partner associate devices before shipment?

At this time, device uploads are only supported through Intune. In the future, OEMs and partners will also be able to pre-associate devices.

### Are virtual machines supported for testing?

No. Device association requires a physical Windows 11 device with TPM 2.0 in a good state. This is the only way to guarantee that the device identity can be securely verified.