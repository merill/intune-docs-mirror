---
layout: Conceptual
title: Windows Autopilot device guidelines | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/autopilot-device-guidelines
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
description: Learn all about hardware, firmware, and software best practices for Windows Autopilot deployment.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: troubleshooting
locale: en-us
document_id: ca348b09-f9b3-b1de-4adf-3516290837fd
document_version_independent_id: ca348b09-f9b3-b1de-4adf-3516290837fd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/autopilot-device-guidelines.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: autopilot-device-guidelines
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/autopilot-device-guidelines.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2aed453f-7d6f-e509-4836-11054d95e2d5
---

# Windows Autopilot device guidelines | Microsoft Learn

## Hardware and firmware best practice guidelines for Windows Autopilot

All devices using Windows Autopilot should meet the minimum hardware requirements for Windows. For more information, see:

- [Find Windows 11 specs, features, and computer requirements](https://www.microsoft.com/windows/windows-11-specifications).
- [How to Find Windows 10 Computer Specifications & Systems Requirements](https://www.microsoft.com/windows/windows-10-specifications).
- [Windows minimum hardware requirements](/en-us/windows-hardware/design/minimum/minimum-hardware-requirements-overview).
- [Windows 11 requirements](/en-us/windows/whats-new/windows-11-requirements).

The following best practices ensure that devices can easily be provisioned as part of the Windows Autopilot deployment process:

- TPM 2.0 is enabled and in a good state on devices intended for Windows Autopilot self-deploying mode. The TPM shouldn't be in the **Reduced Functionality Mode** state.
- The OEM should provision either of the following information into the [SMBIOS fields](/en-us/windows-hardware/drivers/bringup/smbios). The information should follow Microsoft specifications (Manufacturer, Product Name, and Serial Number stored in SMBIOS Type 1 04h, Type 1 05h, and Type 1 07h).

    - Unique tuple info (SmbiosSystemManufacturer, SmbiosSystemProductName, SmbiosSystemSerialNumber)
    - PKID + SmbiosSystemSerialNumber
- Before an OEM ships devices to a Windows Autopilot customer or channel partner, they should upload 4K Hardware Hashes to Microsoft by using the CBR report. The hashes should be collected using the OA3 Tool RS3+ run in Audit mode on full OS.
- Microsoft requires that OEM shipping drivers get published to Windows Update within 30 days of the CBR submission date. System firmware and driver updates are published to Windows Update within 14 days.
- The OEM ensures that the PKID provisioned in the SMBIOS is passed on to the channel.
- When using a VM for Windows Autopilot testing, assign at least 2 processors and 4gb of memory.

## Software best practice guidelines for Windows Autopilot

- The Windows Autopilot device should be preinstalled with only a Windows base image plus drivers.
- Licensed versions of Office, such as [Microsoft 365 Apps for enterprise](/en-us/deployoffice/about-office-365-proplus-in-the-enterprise), can be preinstalled.
- Unless explicitly requested by the customer, no other preinstalled software should be included.

    - Per OEM Policy, Windows features, including built-in apps, shouldn't be disabled or removed.