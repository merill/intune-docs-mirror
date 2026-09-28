---
layout: Conceptual
title: Overview of device enrollment for Android - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/benefits-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn about device enrollment for Android devices, including the benefits and why workplaces and schools require it.
ms.date: 2025-09-03T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: e64be501-f98c-57ee-4a0f-9480b7da5e55
document_version_independent_id: e64be501-f98c-57ee-4a0f-9480b7da5e55
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/benefits-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/benefits-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/benefits-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a75cec46-d9d7-9afc-fa6a-f7e96f362666
---

# Overview of device enrollment for Android - Microsoft Intune | Microsoft Learn

By enrolling your device in Intune, you get secure access to work or school apps on your Android device, and access to apps in Intune Company Portal and the Microsoft Intune app. The Company Portal app and Intune app also monitor your device settings to make sure they meet your organization's requirements and syncs things (like apps, policies, and updates) from your organization to your device.

Important

Before setting up Microsoft Intune for an Android Open Source Project (AOSP) device, ensure your device is supported. For a list of supported devices, see to [Android Open Source Project Supported Devices](../../fundamentals/aosp-supported-devices).

This article provides an overview of device enrollment, its purpose, and its benefits. To skip this overview and go straight to the enrollment steps, select from one of the following articles (ask your IT support person if you're not sure which set of instructions you're supposed to follow):

- Enrollment with Intune Company Portal app
    - [Android work profile for personal devices](enroll-work-profile-android)
    - [Android device administrator for personal and corporate-owned devices](enroll-company-portal-android)
- Enrollment with Microsoft Intune app
    - [Enroll corporate-owned Android device](enroll-intune-app-android)
    - [Enroll corporate-owned AOSP device](enroll-aosp)
- Derived credentials enrollment (smart card users):
    - [Entrust](enroll-entrust-datacard-android)
    - [Intercede](enroll-intercede-android)
    - [DISA Purebred](enroll-disa-purebred-android)

## Secure your device

Use the Company Portal or Microsoft Intune app to enroll and register your personal or work-provided device with your organization. The apps walk you through each step of enrollment, and configure your device settings to match your organization's policies. They also alert you to problems or settings that need to be resolved before you can get corporate access.

Examples of policies that your organization might require are:

- Setting up a password or PIN
- Restricting access after a set number of sign-in attempts
- Ensuring that you're not using a jailbroken or rooted device
- Installing work-required apps

## Access internal apps, VPN, and Wi-Fi

During enrollment, you have to sign in with your work or school account. After you authenticate and configure your device settings to match your organization's policies, you can access your work email, Wi-Fi network, files, and apps on your device. Your organization may also require you to install work or security apps, such as Microsoft Office or Microsoft Defender for Endpoint. You can find all required and available apps in the Company Portal or Microsoft Intune app.

## Remotely reset a lost or stolen device (if device supports it)

If a device is lost or stolen, you can sign in to the Company Portal app or Company Portal website on any other device, and reset your phone to factory settings. This feature is helpful if your missing device contains proprietary work data that you don't want anyone else to access. Because the device is enrolled in management, your support person or IT admin can also help reset it.

The reset feature isn't available in the Microsoft Intune app.

## Get latest policy updates and requirements

The Company Portal or Microsoft Intune app automatically checks in, or syncs, your device with Intune every eight hours. If you're using Company Portal and want to check in more frequently, you or your support person can initiate a manual sync. During check-in, the apps:

- Download available policy and app updates.
- Send hardware inventory updates. These updates don't contain personal information.
- Send company app inventory updates. These updates don't contain personal information.

When your device is out-of-sync or no longer meets the requirements, its status appears in Company Portal or the Intune app as *not compliant*. Device access to work and school-related resources might be revoked until your device meets the requirements again. The Company Portal app notifies you of these problems and the steps you need to take to fix them.

## Get Remote Help from IT support person

When you enroll your device, your company support or IT admin is given access to the device for limited and meaningful reasons. They can:

- Reset your device back to the manufacturer's defaults. As mentioned above, you also have access to reset your device. However, if you can't access the Company Portal app right away, your company can reset the device for you.
- Remove all company-related data. Your organization might remove company-related data from your device if you leave the company, or if your device becomes unmanaged. Your personal data and settings aren't removed, and will remain on the device.
- Set requirements for your device, such as requiring you to have a device password or PIN. In this case, you'll get app notifications that your device isn't compliant. Your company support might also limit the number of times you can enter an incorrect password on your device. Excessive, failed password attempts might result in your device being locked.
- Require you to accept terms and conditions.
- Disable the camera. The purpose of this policy is to prevent you from photographing proprietary information, and also to remove distractions from school environments. Schools might disable cameras on classroom devices so that students cannot share test materials.
- Require that all data on the device is encrypted. If lost or stolen, this policy helps protect the data on your device. It also protects data that is shared between devices or apps.