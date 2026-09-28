---
layout: Conceptual
title: Your Android device seems to be encrypted - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/security/troubleshoot-encryption-status-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Resolve encryption status in Company Portal and Microsoft Intune app
ms.date: 2025-09-03T00:00:00.0000000Z
ms.reviewer: rishitasarin
locale: en-us
document_id: 17d61894-429b-8f01-e78a-5954c05298ac
document_version_independent_id: 17d61894-429b-8f01-e78a-5954c05298ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/security/troubleshoot-encryption-status-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/security/troubleshoot-encryption-status-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/security/troubleshoot-encryption-status-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 28f32308-6384-828f-4d2a-cb07c3c243c0
---

# Your Android device seems to be encrypted - Microsoft Intune | Microsoft Learn

If Company Portal or the Microsoft Intune app say that your Android device isn't encrypted, but you're sure that it is, try the steps in this article.

## Add a startup PIN

Certain Android devices require you to create a startup PIN for security purposes. The location of this setting will be in your device's **Settings** app. The name and location of the setting could vary. For example, on the Samsung Galaxy S7, the setting is referred to as **Secure Startup**. To enable it and create a passcode, go to **Settings** &gt; **Lock Screen and Security** &gt; **Secure Startup**.

## Encrypt the entire device

This section only applies to the Company Portal app. Some devices will give you a choice between encrypting the entire device or just the used space. Choose the option to encrypt the entire device. If you selected to encrypt only the used space:

1. [Remove this device from the Company Portal](../unenrollment/unenroll-android).
2. Decrypt the used space.
3. Encrypt the entire device.
4. Re-enroll the device.

## Downgrade your version of Android

This section only applies to the Company Portal app. If your device offers you the option to downgrade to Android 8.0 or later, then do so. There is a risk of data loss if you try to downgrade your device. Otherwise, we recommend that you contact your company support to resolve this issue. Get contact information for your company support on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).

## Specific manufacturer issues

Some Android devices on version 7.0 and later encrypt data in ways that are inconsistent with certain Android platform standards. These encryption methods put device information at risk. As a result, these devices aren't supported.

For a non-exhaustive list of supported Android devices, see the article [Supported operating systems and browsers in Intune](../../fundamentals/ref-supported-platforms#supported-samsung-knox-standard-devices). If your device isn't listed, refer to the device manufacturer or contact your support person.

Note

Microsoft works with manufacturers to address any issues we find while testing or that users report to us. We update this article whenever new information is available.

## Update devices

If you haven't updated your device to the most recent version of Android, go to your device's **Settings** app and select **Update**.