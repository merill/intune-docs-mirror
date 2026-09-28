---
layout: Conceptual
title: What info can your organization see when you enroll your device? - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/data-visibility
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes the information on your enrolled device that's visible to your organization.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: 9342c904-df3b-12c4-7341-c0272e715388
document_version_independent_id: 9342c904-df3b-12c4-7341-c0272e715388
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/data-visibility.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/data-visibility
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/data-visibility.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9250b7b8-0071-e55c-fd61-93ee8d49fd91
---

# What info can your organization see when you enroll your device? - Microsoft Intune | Microsoft Learn

**Applies to**:

- Windows
- Android
- iOS/iPadOS
- macOS
- Linux

Your organization can't see your personal information when you enroll a device in Microsoft Intune. Enrolling your device makes certain information such as device model and serial number visible to IT administrators and support people with administrator access.

- **Support person**: This is the person or department at your organization that you're supposed to contact if you're having problems with your device. They provide technical support for device setup, enrollment, and access.
- **IT administrator**: *IT admin* for short, this person or team of people configures the Microsoft Intune device management and enrollment settings for your organization. Some IT admins also provide technical support.

This article describes everything your organization can and can't access on an enrolled device, and explains why certain data is made visible. To view the ownership type for an enrolled device, sign in to the Intune Company Portal app or website and go to **Device Details**.

## Things your organization can never see

Your organization can't see:

- Calling and web browsing history
- Email and text messages
- Contacts
- Calendar
- Passwords
- Pictures, including what's in the photos app or camera roll
- Content of user-created documents

## Things your organization can always see

Your organization can always see:

- Device owner
- Device name
- Device serial number
- Device model, such as *Google Pixel*
- Device manufacturer, such as *Microsoft*
- Operating system and version, such as *iOS 12.0.1*
- Device IMEI

## Things your organization might see

Your organization can see and access certain aspects of your device when assisting with or troubleshooting device setup. This section describes the type of information available.

### Phone number

Your organization can see the full phone number of all corporate-owned devices, except for Android devices with a work profile, which only show the last four digits. They can see the last four digits of a personal device's phone number.

### Device storage space

If you have trouble installing a required app, your support person might look at your storage size to find out if low space is the cause.

### Location

Your organization can view a lost corporate-owned device's location. They can't view a personal device's location.

If necessary, your organization can put a missing, corporate-owned iPhone or iPad into *managed lost mode*. This mode lets your organization request the device location. When someone requests access to the device location, the device locks and a message appears on the lock screen to explain what's happening. For information about *supervision*, which is another type of configuration for corporate-owned Apple devices, see [Get started with a supervised iPhone or iPad](https://go.microsoft.com/fwlink/?linkid=853816) in the Apple support docs.

### App inventory details

On corporate-owned Android devices that have a work profile, your organization can only see the apps installed in the work profile. For all other corporate-owned devices, they see all installed apps.

On personal devices, your organization can see the managed app inventory, which includes work and school apps. Some configurations allow organizations to see more than just the managed app inventory on a personal device. To learn more about the information your organization collects, contact your IT admin.

Note

An app is considered a *managed app* when it's installed in one of the following ways:

- You install it from the Company Portal app after your organization makes it available to you.
- Your organization requires you to have a certain app for work and school and automatically installs it on the device upon enrollment.

### App permissions

Note

This information applies to devices running Android 11 and earlier.

An IT admin can grant permission to apps in the work profile, both manually and by automation. The IT admin does this to reduce the number of prompts you receive. The permissions could be for things like the camera, microphone, and location. If your device is running Android 11, you receive a push notification when someone grants permission to an app.

### Network information

Some information about network connections for Android devices may be available to your organization. For example, if your organization requires devices to remain within a certain building, your device would identify the network where it's connected.

### Additional device details

Your organization can query these details about a corporate-owned Windows device.

- Hardware and operating system environment information
- Installed certificate details
- File paths and file names
- Operating system user and group information
- Registry and event log entries
- Details about running processes

For more information, see [Device Query](../../advanced-analytics/device-query).