---
layout: Conceptual
title: Encrypt your Android device - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/security/enable-encryption-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to turn on Android device encryption when required by Intune.
ms.date: 2024-11-07T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: 28a6228c-7573-888d-ed94-ea74116fdb90
document_version_independent_id: 28a6228c-7573-888d-ed94-ea74116fdb90
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/security/enable-encryption-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/security/enable-encryption-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/security/enable-encryption-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 16850944-68ae-8069-c5c8-d06c3905d2c8
---

# Encrypt your Android device - Microsoft Intune | Microsoft Learn

Device encryption protects your files and folders from unauthorized access if your device is lost or stolen. It makes the data inaccessible and unreadable to people who don't have a passcode.

Before you can access school or work resources, your organization might require you to:

- Encrypt your device
- Enable secure startup
- Set a lock screen and startup PIN

Note

Certain Android devices from Huawei, Vivo, and OPPO can't be encrypted. For more information, see [Device encrypted but app says otherwise](troubleshoot-encryption-status-android).

## Encrypt device

Follow these steps to encrypt your device. Your device may restart more than once. The name and location of the encryption option varies depending on your device manufacturer and Android version. These steps don't apply to newer Android devices, which are encrypted by default when you set up a lock screen.

1. Open the **Settings** app.
2. Type **security** or **encrypt** in the search bar to find related settings.
3. Tap the option to encrypt your device. Follow the onscreen instructions.
4. When prompted, set a lock screen password, PIN, or other authentication method (if allowed by your organization).
5. To recheck settings, open the Company Portal or Microsoft Intune app.
    - Company Portal users: Select your device and tap **Check device settings**.
    - Microsoft Intune users: You'll have to wait until the page updates, but when it does, your encryption status should change to compliant.

## Enable secure startup

Secure startup protects your device by requiring a password or PIN each time the device is turned on. The name and location of the secure startup option can vary depending on your device manufacturer and Android version.

1. Open the **Settings** app.
2. Type **secure startup** in the app's search bar. a. If that doesn't bring up a matching result, try searching for **Strong protection**.
3. Tap **Secure startup** &gt; **Require PIN when device turns on**.
4. When prompted, enter your device PIN.
5. If you're going through device setup/enrollment, return to the app and select **CONTINUE**. If you received this message outside or after enrollment:
    - Company Portal app users: Open the app, select your device, and then tap **Check device settings**.
    - Microsoft Intune app users: Open the app, wait until the screen loads, and then your encryption status should change to compliant.

## Set lock screen

Add a device PIN, password, or other authentication method (if allowed by your organization) to the device. The lock screen appears and prompts for your credentials when you turn on the device and when the device is idle. To set up a lock screen, go to **Settings** &gt; **Security and privacy** &gt; **Lock screen**.

## Troubleshoot

**Issue**: The encryption button is disabled.

**Thing to try**: Make sure your device is fully charged and plugged in. Encryption could take a while and requires a full battery.

**Issue**: You see a message saying that you still need to encrypt your device.

**Things to try**:

- Set a lock screen on your device.
- Enable secure startup.

Still need help? Contact your IT support person. Check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) or app for your organization's contact information.