---
layout: Conceptual
title: Android (AOSP) compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-aosp-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- compliance
- sub-device-compliance
ms.subservice: protect
description: View the device compliance settings for Android (AOSP) that you can manage with Microsoft Intune compliance policies.
ms.date: 2025-09-04T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: tycast
locale: en-us
document_id: 34fa0848-bba1-8928-ec32-2eb2ee6485b1
document_version_independent_id: 34fa0848-bba1-8928-ec32-2eb2ee6485b1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/ref-android-aosp-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/ref-android-aosp-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/ref-android-aosp-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 505158d7-6d2d-0c0a-3d52-8c4fcce279ea
---

# Android (AOSP) compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

This article lists the compliance settings you can configure for Android (AOSP) devices in Intune. Use these settings as part of your mobile device management (MDM) solution to define your organization's standards for:

- Device health
- Device properties
- System security

Devices are also governed by tenant-wide [compliance policy settings](overview#compliance-policy-settings).

This feature applies to:

- Android (AOSP)

Settings in this article are organized by the sections that appear in the admin center when you create a compliance policy.

## Before you begin

To access these settings, [create an Android (AOSP) compliance policy](create-policy#create-the-policy). When prompted to select a **Platform**, choose **Android (AOSP)**.

## Device health

- **Rooted devices** Prevent rooted devices from having corporate access.

    - **Not configured** (*default*) - This setting isn't evaluated for compliance or noncompliance.
    - **Block** - Mark rooted devices as noncompliant.

## Device properties

- **Minimum OS version** When a device doesn't meet the minimum OS version requirement, it's reported as noncompliant. A link with information about how to upgrade is shown. The end user can choose to upgrade their device, and then get access to company resources.

    By default, no version is configured.
- **Maximum OS version** When a device is using an OS version later than the version specified in the rule, access to company resources is blocked. The user is asked to contact their IT admin. Until a rule is changed to allow the OS version, this device can't access company resources.

    By default, no version is configured.
- **Minimum security patch level** Enter the oldest security patch level a device can have. Devices that aren't at least at this patch level are noncompliant. The date must be entered in the `YYYY-MM-DD` format.

    By default, no patch level is configured.

## System security

If you don't configure password requirements, the use of a device password is optional and left up to the users to configure.

- **Require a password to unlock mobile devices** Require users to have a password-protected lock screen on their device. Your options:

    - **Not configured** (*default*) - This setting isn't evaluated for compliance or noncompliance.
    - **Yes** - Users must enter a password to unlock their devices.

    If you require a password, also configure:

    - **Required password type** Require users to use a certain type of password. Your options:

        - **Device default** - To evaluate password compliance, be sure to select a password strength other than *Device default*.
        - **Numeric** - Password must only be numbers, such as `123456789`.

            Also enter:

            - **Minimum password length**: The minimum number of digits required, from 4 to 16.
        - **Numeric complex** - Repeated or consecutive numerals, such as `1111` or `1234`, aren't allowed.

            Also enter:

            - **Minimum password length**: The minimum number of digits required, from 4 to 16.

        Note

        There is a known issue that prevents **Password required, no restriction** from working on Android (AOSP) devices.

        The following password types are listed as options but are not supported for Android (AOSP) devices: *Alphabetic*, *Alphanumeric*, and *Alphanumeric with symbols*.
    - **Maximum minutes of inactivity before password is required** Enter the maximum idle time allowed, from 1 minute to 8 hours, before the user must re-enter their password to get back into their device. When you choose **Not configured** (default), this setting isn't evaluated for compliance or noncompliance.

## Encryption

- **Require encryption of data storage on a device** Your options are:

    - **Not configured** (*default*) - This setting isn't evaluated for compliance or noncompliance.
    - **Yes** - Encrypt data storage on your devices. Devices are encrypted when you set the **Require a password to unlock mobile devices** setting equal to **Yes**.

## Device compliance reporting

Compliance reports are currently not available for Android (AOSP) devices. This section will update when reporting becomes available.