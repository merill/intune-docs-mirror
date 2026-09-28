---
layout: Conceptual
title: Get Mac recovery key from Intune Company Portal website - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/security/collect-recovery-key-company-portal-website
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Get the recovery key for your work or school device on the Company portal website.
ms.date: 2024-11-08T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: 82cb864f-0b32-babd-e619-14368ebb6ef2
document_version_independent_id: 82cb864f-0b32-babd-e619-14368ebb6ef2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/security/collect-recovery-key-company-portal-website.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/security/collect-recovery-key-company-portal-website
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/security/collect-recovery-key-company-portal-website.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 47df84e2-ccdf-a64d-2296-94ab290081cd
---

# Get Mac recovery key from Intune Company Portal website - Microsoft Intune | Microsoft Learn

Get the recovery key for your locked Mac. If you forget the password on the Mac you use for work or school and are locked out, you can sign in to the Company Portal on another device to retrieve your key.

## Get recovery key from Company Portal website

This option is available for Macs that were encrypted by your organization using FileVault. It's not available for Macs that you have personally encrypted.

1. On any device, sign in to the [Company Portal website](https://portal.manage.microsoft.com).
2. Open the menu and go to **Devices**.
3. Select the Mac you're locked out of.
4. Select **Get recovery key**.

    ![Screenshot of Company Portal website, highlighting Get recovery key section.](media/collect-recovery-key-company-portal-website/1907-recovery2-cpweb-intune.png)
5. Your recovery key appears. For security reasons, the key disappears after five minutes. To see the key again, select **Get recovery key**.

    ![Screenshot of Company Portal website, showing recovery key.](media/collect-recovery-key-company-portal-website/1907-recovery-cpweb-intune.png)

## Get recovery key from Company Portal app

This option isn't available for Macs that you have personally encrypted. The personal recovery key must belong to a device that's enrolled in Microsoft Intune, and encrypted with FileVault through Microsoft Intune.

1. Open the Intune Company Portal app. The following apps support recovery key retrieval:

    - Company Portal for iOS
    - Company Portal for macOS
2. Go to **Devices** and select the Mac you're locked out of.
3. On the device's page, select **Get recovery key**.
4. The Company Portal website opens and shows the key. Write down or copy the key. For security reasons, the key disappears after five minutes.

## IT pro support

If a key isn't found but your device is properly encrypted, contact your organization's support person. For contact information, check for helpdesk details on the Company Portal website.

If you're an IT support person and want to configure and manage FileVault encryption, see [Use FileVault disk encryption for macOS with Intune](../../device-configuration/endpoint-security/encrypt-filevault-macos#monitor-and-manage-filevault).