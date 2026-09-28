---
layout: Conceptual
title: Check device status in Microsoft Intune app for Linux - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/validate-status-linux
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Verify work access and resolve compliance issues in the Intune app for Linux.
ms.date: 2024-10-08T00:00:00.0000000Z
ms.reviewer: arnab
locale: en-us
document_id: 3078137f-e578-3bc6-ea6f-2f1d9c119e45
document_version_independent_id: 3078137f-e578-3bc6-ea6f-2f1d9c119e45
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/validate-status-linux.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/validate-status-linux
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/validate-status-linux.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: ece02765-9c6b-5ead-a580-22f1b431037c
---

# Check device status in Microsoft Intune app for Linux - Microsoft Intune | Microsoft Learn

You can use the Microsoft Intune app for Linux to resolve access and compliance issues for enrolled devices. This article describes how to:

- View the status of a device
- View and resolve compliance issues with your device settings
- Refresh device status

## View device status

The Intune app routinely checks in with your device to verify that it complies with setting requirements. Check-ins occur at the time of enrollment, and thereafter whenever you're using your device for work. The status reveals the result of the last check-in. To view the status of a device, sign in to the Intune app and select the device.

There are three statuses in the Intune app:

- **Compliant** – Your device meets your organization's requirements. It should have access to work or school resources.
- **Checking status** – Intune is checking the device settings.
- **Not compliant** – Your device doesn't meet your organization's requirements. It may be restricted from accessing work or school resources. Additional action is needed from you to update your settings.

## View compliance issues

To view compliance issues:

1. Sign in to the Intune app.
2. Select a device.
3. On the device details page, select **View Issues**. This option is only available when issues are present.

The app shows you the following information:

- The action required, such as *Upgrade your operating system*.
- The reason for noncompliance, such as *This device's operating system is not supported*.
- The **How to resolve this** link that, when available, points to a help article on learn.microsoft.com.

### Operating system and version

When OS and version requirements are enforced, devices running Linux flavors or versions that aren't supported are marked as noncompliant. To resolve this issue, upgrade to or install a version that's supported by your organization.

Contact your support person for more information about your organization's OS requirements.

### Password complexity

When password complexity requirements are enforced, devices with weak passwords are marked as noncompliant. To resolve this issue, update your device password so that it meets your organization's requirements for length and quality.

### Device encryption

When encryption requirements are enforced, devices that aren't encrypted are marked as noncompliant. To resolve this issue, encrypt the local data on your device in accordance with your organization's encryption policies.

Not all filesystem partitions need to be encrypted:

- Read-only partitions are ignored.
- Pseudo-filesystems (such as */proc* or *tmpfs*) are ignored.
- The */boot* or */boot/efi* partitions are ignored.

Intune supports all encryption systems that use the [*dm-crypt* subsystem](https://gitlab.com/cryptsetup/cryptsetup/-/wikis/DMCrypt), the standard underlying infrastructure for Linux systems. We recommend setting up dm-crypt by using the *LUKS format* with the *cryptsetup tool*.