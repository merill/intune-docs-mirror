---
layout: Conceptual
title: Automatically enroll devices with Samsung Knox Mobile Enrollment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-samsung-knox-mobile
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Learn how to enroll Android devices in Microsoft Intune with the Knox Mobile Enrollment tool.
ms.date: 2023-12-01T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: abigailstein
locale: en-us
document_id: 62ac626b-4450-3b64-5b99-665796b66838
document_version_independent_id: 62ac626b-4450-3b64-5b99-665796b66838
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/setup-samsung-knox-mobile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/setup-samsung-knox-mobile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/setup-samsung-knox-mobile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 38294de6-3092-dd2d-f3fb-8febd632bea2
---

# Automatically enroll devices with Samsung Knox Mobile Enrollment - Microsoft Intune | Microsoft Learn

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Use Samsung Knox Mobile Enrollment as a tool to bulk enroll enterprise devices in Microsoft Intune. Knox Mobile Enrollment enables device enrollment to happen straight out-of-the-box after you turn on the device. Enrollment is supported for the following Android Enterprise device types:

- Dedicated devices
- Fully managed devices
- Corporate-owned devices with a work profile

You must have a Samsung Knox account to access Knox Mobile Enrollment services in the Knox Admin Portal. Samsung Knox accounts require approval from Samsung, which can take one to two business days.

## Create profile

To use Microsoft Intune and Knox Mobile Enrollment together, create a profile in the Knox Admin Portal. Add Microsoft Intune to the profile as your enterprise mobility management (EMM) solution.

**Custom JSON data** appears optional in the Knox Admin Portal, but Microsoft Intune requires it for a successful enrollment. Enter the following JSON data:

`{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "enter Intune enrollment token string"}`

Add your enrollment token to the string where indicated. Additionally, configure these device settings in the profile:

- **QR code for enrollment** (optional): Add a QR code to speed up device enrollment.
- **System applications**: Leave all system apps enabled to ensure all apps are available in the profile. If you don't select this value, some default system apps are excluded from the apps tray.
- **Company name**: Enter your organization's name. The name appears onscreen during device enrollment.

## Upload devices

Assign your profile to Android devices uploaded in the Knox Admin Portal. Supported upload methods include:

- Samsung-approved resellers: A Samsung-approved reseller can automatically upload your organization's purchased devices in the Knox Admin Portal, where you can manage them. Use this option if you purchase devices through a Samsung-approved reseller.
- Knox Deployment App: You don't need to work with a reseller to upload devices in the Knox Deployment App. We recommend using the app for enrolling existing devices that were previously set up in Knox Mobile Enrollment. You can use Bluetooth or NFC to add devices to the Knox Admin Portal.

## Resources

For more information about Knox Mobile Enrollment setup and requirements, see:

- [Get started with Knox Mobile Enrollment](https://docs.samsungknox.com/admin/knox-mobile-enrollment/get-started/get-started-with-knox-mobile-enrollment/)
- [About Knox Deployment App](https://docs.samsungknox.com/admin/knox-mobile-enrollment/about-kda.htm)