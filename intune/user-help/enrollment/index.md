---
layout: Conceptual
title: What is device enrollment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn what it means to enroll your device with the Company Portal and Microsoft Intune app.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: bbc5d727-5148-b0f8-ce71-5106fc021126
document_version_independent_id: 2329e747-6727-983e-bf7a-9001ab747c03
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 190bd024-d694-077a-b20e-a90fbce63435
---

# What is device enrollment - Microsoft Intune | Microsoft Learn

**Applies to**:

- Android
- iOS/iPadOS
- Linux
- macOS
- Windows

Device enrollment lets you access your work or school's internal resources (such as apps, Wi-Fi, and email) from your mobile device. During device enrollment:

- Your device enrolls in Microsoft Intune, a mobile device-management provider, and registers with your organization. This step ensures that you're authorized to access your organization's email, apps, and Wi-Fi.
- Your organization's device-management policies are applied to your device. Policies can include requirements for things like device passwords and encryption. The purpose of these requirements is to keep your device and your organization's data secure from unauthorized access.

Once you update your device settings to meet your organization's requirements, enrollment is complete. You can securely sign in to your work or school account from virtually anywhere.

This article describes other aspects of enrollment, such as how to get the apps, supported devices, and removing or resetting your device.

## Company Portal and Microsoft Intune app

Company Portal and the Microsoft Intune app alert you to policy or setting changes so you can take action without losing access to work or school.

Company Portal keeps your personal and work information separate so you can remain productive and focused when using your device for work purposes. You can also find your work and school apps in Company Portal.

### Get Company Portal

In some cases, your organization installs the Company Portal app on your device for you, so check your device before you try to install it. The app is also available to install from app stores such as the Microsoft Store, App Store, and Google Play store. To access the Company Portal from a web browser, sign in to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) with your work or school account.

### Get Microsoft Intune app

If you're required to use the Microsoft Intune app with your Android device, your organization installs it on your device for you.

For information about how to install the Intune app on a work or school-provided Linux device, see [Get the Microsoft Intune app for Linux](../company-portal/intune-app-linux).

## What's the difference between the apps and the website?

The Company Portal app is available for Windows, iOS/iPadOS, macOS, and Android devices. It integrates seamlessly with your device's respective platform. The website version is accessible from any device and gives you the same universal experience no matter what device you're using.

The Microsoft Intune app is for Linux devices and corporate-owned Android and AOSP devices. It doesn't have a website.

## What kind of devices can you enroll with Company Portal?

You can use Company Portal to enroll devices running:

- Windows
- Android OS
- iOS/iPadOS
- macOS

## What kind of devices can you enroll with the Microsoft Intune app?

You can enroll corporate-owned Android and AOSP devices that your organization has set up to use with the app. The app supports Android 8.0 and later. The Microsoft Intune app is also available for Linux devices. Enrolled Linux devices are considered corporate-owned in Intune, so we don't recommend enrolling a personal device.

## Can you remove a device from the Company Portal?

You can remove or reset your device with Company Portal. There is a difference between *remove* and *reset*.

During removal, Company Portal unenrolls and unregisters the device from Intune. That device loses access to the Company Portal. Work and school data might also be removed.

During a device reset, Company Portal tries to reset your device back to the manufacturer's factory default settings. All data is removed from the device. A reset is useful if, for example, you lose your device and there is sensitive data on it. You can remotely reset an enrolled device from the Company Portal website.

## Can you remove a device from the Microsoft Intune app?

No, there's no way for you to remove a corporate-owned device from the Microsoft Intune app.

## What if I can't see my device in the Company Portal or Microsoft Intune app?

To see a device in Company Portal, it must first be enrolled. If you still don't see all of your devices after enrollment, try to sync or check access through the Company Portal. You won't see devices that are owned and managed by your company.

In the Microsoft Intune app, you only see the device you're currently using. Other enrolled devices aren't visible to you in the app.

## Where else can I go for help?

Refer to the articles in this document set for step-by-step help and explanations. In the table of contents, select from the Android, iOS, Windows, or macOS device management categories, then select **Update device settings** to see a list of how-to articles that address common messages in Company Portal.

You can also contact your IT support person. The Company Portal and Microsoft Intune apps offer help and support pages with contact information and ways to report a problem. Contact information is also available on your org's [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).