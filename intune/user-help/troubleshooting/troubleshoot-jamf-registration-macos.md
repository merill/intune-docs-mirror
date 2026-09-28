---
layout: Conceptual
title: Resolve enrollment issues on Macs integrated with Jamf - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/troubleshooting/troubleshoot-jamf-registration-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Resolve Intune Company Portal device registration issues on Macs managed by Jamf Pro.
ms.date: 2025-09-03T00:00:00.0000000Z
ms.reviewer: beflamm
locale: en-us
document_id: 9195c6c1-6575-f013-f14f-b3a8f70ec9e0
document_version_independent_id: 9195c6c1-6575-f013-f14f-b3a8f70ec9e0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/troubleshooting/troubleshoot-jamf-registration-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/troubleshooting/troubleshoot-jamf-registration-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/troubleshooting/troubleshoot-jamf-registration-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 82a6d539-7eec-5c2d-9bf4-7f8f479651a1
---

# Resolve enrollment issues on Macs integrated with Jamf - Microsoft Intune | Microsoft Learn

**Applies to macOS**

This article is for employees and students setting up a Mac for work or school access using Intune Company Portal, and describes how to resolve device registration issues on Macs managed by Jamf Pro. The Intune Company Portal app flags Jamf Pro-managed devices for the following device registration issues:

- Account not onboarded.
- Device is already enrolled.

## Account not onboarded

For a device to successfully enroll and register for work, you must use Jamf Self Service to open the Intune Company Portal. If you open the Company Portal app any other way, the device enrolls and registers without its connection to Jamf, which results in the *Account not onboarded* message.

To resolve this issue, exit Company Portal. Then open the Jamf Self Service app and select the Company Portal app that's available there to begin device registration.

## Device is already enrolled

The following actions may result in multiple instances of your device showing up in the Intune Company Portal and failed enrollment:

- The device you're using was previously enrolled, and it unenrolled from the Jamf service correctly but didn't successfully unenroll from the Microsoft Intune service.
- Several attempts to register the device were made.

Contact your support person for help with unenrolling your device, or see [Troubleshoot Jamf Pro integration- The device was previously enrolled in Intune](/en-us/troubleshoot/mem/intune/device-protection/troubleshoot-jamf#cause-6---the-device-was-previously-enrolled-in-intune) for steps to properly unenroll the device. Sign in to the Intune Company Portal app or [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) and go to **Help & support** for your organization's support information.