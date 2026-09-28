---
layout: Conceptual
title: Overview of device enrollment for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/overview-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes what happens after you enroll your device in Intune, for Windows.
ms.date: 2025-09-03T00:00:00.0000000Z
ms.reviewer: madakeva
locale: en-us
document_id: dde515a2-5969-99e2-782a-b81ddeb81bdd
document_version_independent_id: dde515a2-5969-99e2-782a-b81ddeb81bdd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/overview-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/overview-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/overview-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7edc3307-437e-5643-ac53-b8241b89aa41
---

# Overview of device enrollment for Windows - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

By enrolling your device in Intune, you get secure access to work or school apps on your mobile device, and access to apps in Intune Company Portal. The Company Portal app also monitors your device settings to make sure they meet your organization's requirements, and syncs things (like apps, policies, and updates) from your organization to your device.

This article describes what to expect once you've enrolled your device for work.

## What happens on all devices after enrollment

After you enroll a device for work or school using Intune Company Portal:

- You can access your org's network, email, and work files on the device.
- You can install work or school apps from the Company Portal website and app, and access them by signing in to your work or school account.
- Your work or school email is automatically set up.
- You can reset your phone to factory settings if it's lost or stolen.

### What happens on Windows PCs after enrollment

In addition to everything under [What happens on all devices after enrollment](overview-windows#what-happens-on-all-devices-after-enrollment), after you enroll a Windows device in Intune:

- Software installs on the device that enables your organization to manage the device. Your support person can automatically update this software.
- If your organization requires it, anti-malware and virus software is installed on the device.
- Intune requires access to the hard drive so that it can verify that the device meets device and security requirements. This is the same kind of access that Intune needs on a mobile device (for example, on an Android or iOS device). IT support can't view or make changes to anything on your hard drive.
- Your IT support person can install work apps and updates on your device.

## IT support permissions

When you enroll your device, you are giving IT support permission to:

- Reset your device back to the manufacturer's default settings. This is helpful if the device is lost or stolen.
- Remove work-related files and business apps. Personal data and settings aren't removed.
- See the software installed on the device, including software you've personally installed.
- Set requirements on your device, like requiring you to have a device password or PIN. As another example, your org could limit how many times you can enter an incorrect password, and lock you out of the device after too many failed attempts.
- Require you to encrypt the data on your device to help protect company data, in case your device is lost or stolen.
- Require you to accept terms and conditions.
- Block you from using the device camera or screenshot feature. This restriction limits the sharing of work-related data.

## Device syncing for updates

Every eight hours, enrolled devices sync with Intune to get the latest updates and policies from your org. During check-in the device can:

- Download policy or app updates.
- Receive hardware inventory updates.
- Receive app inventory updates.