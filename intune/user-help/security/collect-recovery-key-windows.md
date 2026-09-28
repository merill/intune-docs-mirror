---
layout: Conceptual
title: Get BitLocker recovery key for enrolled device - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/security/collect-recovery-key-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Get a BitLocker recovery key for your work or school device from the Company portal website or apps.
ms.date: 2024-11-08T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: 5a2e3468-b8c3-d997-0513-5278e10d1f46
document_version_independent_id: 5a2e3468-b8c3-d997-0513-5278e10d1f46
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/security/collect-recovery-key-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/security/collect-recovery-key-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/security/collect-recovery-key-windows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a67bd0a8-ced0-6862-d6f2-c4c4003ce02f
---

# Get BitLocker recovery key for enrolled device - Microsoft Intune | Microsoft Learn

Access the BitLocker recovery key for a work or school device on the Intune Company Portal website or in the Intune Company Portal app. If you forget the sign-in password and get locked out of an Intune-enrolled PC, you can unlock it with a stored recovery key. This article describes how to retrieve the key from Company Portal.

Note

A BitLocker key is a 48-character long password divided into eight groups of 6 characters separated by dashes. Example: *123456-789012-345678-901234-567890-123456-789012-345678*

## Requirements

- Enrolled, BitLocker-encrypted work or school device provided by your organization
- Registered work or school account
- Permission to view BitLocker recovery key
- Supported devices
- Supported version of Company Portal app

You can obtain the recovery key for a work or school device that's encrypted by your organization. Recovery keys aren't available for devices you personally encrypt.

## Get recovery key from Company Portal website

Retrieve a personal BitLocker recovery key on the Company Portal website.

![Example screenshot of the BitLocker Recovery Key page on the Intune Company Portal website. ](media/collect-recovery-key-windows/get-recovery-key-company-portal-website.png)

1. On any device, sign in to the [Company Portal website](https://portal.manage.microsoft.com).
2. Go to **Devices**.
3. Select the PC you're locked out of.
4. Select **Get recovery key**.
5. Select **Show recovery key**.
6. Your recovery key appears. Write down or copy the code, and then enter it in the BitLocker recovery screen on your computer. For security reasons, the key disappears after five minutes. To see the key again, select **Show recovery key**.

If a key isn't found, but your device is properly encrypted, contact your IT support person for help. Check the Company Portal website for your organization's helpdesk details.

## Get recovery key from Company Portal app

Retrieve a personal BitLocker recovery key in the Company Portal app. The recovery key must belong to a device that's enrolled in Microsoft Intune.

1. Open the Intune Company Portal app. The following apps support recovery key retrieval:

    - Company Portal for iOS
    - Company Portal for macOS
2. Go to **Devices**, and then select your Windows device.
3. On the device details page, select **Get recovery key**. The Company Portal website opens in Safari and shows the key.

After 5 minutes of inactivity, Company Portal returns you to the device page in your web browser. You can view the key again from there.

## IT pro support

If you're an IT support person and want to configure and manage encryption, see [Manage policy for Windows devices with Microsoft Intune](../../device-configuration/endpoint-security/encrypt-bitlocker-windows).