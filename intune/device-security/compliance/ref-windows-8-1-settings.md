---
layout: Conceptual
title: Windows 8.1 compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-windows-8-1-settings
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
description: View the device compliance settings for Windows 8.1 that you can manage with Microsoft Intune compliance policies.
ms.date: 2024-05-15T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 6fcb5755-6026-10bf-672b-f632baf2a98f
document_version_independent_id: 6fcb5755-6026-10bf-672b-f632baf2a98f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/ref-windows-8-1-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/ref-windows-8-1-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/ref-windows-8-1-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: e9baa151-e446-bb30-b803-1ed36697abf8
---

# Windows 8.1 compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.

This article lists and describes the different compliance settings you can configure on Windows 8.1 devices in Intune. As part of your mobile device management (MDM) solution, use these settings to block simple passwords, set a minimum and maximum OS version, and more.

This feature applies to:

- Windows 8.1 and later

As an Intune administrator, use these compliance settings to help protect your organizational resources. To learn more about compliance policies, and what they do, see [get started with device compliance](overview).

## Before you begin

[Create a compliance policy](create-policy#create-the-policy). For **Platform**, select **Windows 8.1 and later**.

## Device Properties

### Operating System Version

- **Minimum OS version**: Enter the minimum allowed version. When a device doesn't meet the minimum OS version requirement, it's reported as noncompliant. A link with information on how to upgrade is shown. The device user can choose to upgrade their device, and then get access to company resources.
- **Maximum OS version**: Enter the maximum allowed version. When a device is using an OS version later than the version entered in the rule, access to organization resources is blocked. The device user is asked to contact their IT administrator. The device can't access organizational resources until a rule changes to allow the OS version.

Windows 8.1 PCs return a version of **3**. If the OS version rule is set to Windows 8.1 for Windows, then the device is reported as noncompliant even if the device has Windows 8.1.

## System Security

### Password

- **Require a password to unlock mobile devices**:

    - **Not configured** (*default*) - This setting isn't evaluated for compliance or noncompliance.
    - **Require** - Users must enter a password before they can access their device.
- **Simple passwords**:

    - **Not configured** (*default*) - Users can create simple passwords like **1234** or **1111**.
    - **Block** - Users can't create simple passwords, such as **1234** or **1111**.
- **Minimum password length**: Enter the minimum number of digits or characters that the password must have.

    For devices that run Windows and are accessed with a Microsoft account, the compliance policy fails to evaluate correctly if either of the following conditions is true:

    - Minimum password length is greater than eight characters
    - Minimum number of character sets is more than two
- **Password type**: Choose if a password should have only **Numeric** characters, or if there should be a mix of numbers and other characters (**Alphanumeric**).

    When set to *Alphanumeric*, the following setting is available.

    - **Number of non-alphanumeric characters in password**: When the *password type* is set to **Alphanumeric**, specify the minimum number of character sets that the password must contain. Options include **0** to **4** sets, with a default of **1**.

        The four character sets are:

        - Lowercase letters
        - Uppercase letters
        - Symbols
        - Numbers

        Setting a higher number requires the user to create a password that is more complex. For devices that are accessed with a Microsoft account, the compliance policy fails to evaluate correctly if either of the following conditions is met:

        - Minimum password length is greater than eight characters
        - Minimum number of character sets is more than two
- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password.
- **Password expiration (days)**: Select the number of days before the password expires, and users must create a new one.
- **Number of previous passwords to prevent reuse**: Enter the number of previously used passwords that can't be used.

### Encryption

- **Encryption of data storage on device**:
    - **Not configured** (*default*)
    - **Require** - Use *Require* to encrypt data storage on your devices.