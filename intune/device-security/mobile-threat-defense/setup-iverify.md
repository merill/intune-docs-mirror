---
layout: Conceptual
title: Set up iVerify Enterprise Mobile Threat Defense with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-iverify
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: How to set up iVerify Enterprise Mobile Security with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2025-12-02T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5501aa37-641b-03c2-2cdc-6cca0ce972fb
document_version_independent_id: 5501aa37-641b-03c2-2cdc-6cca0ce972fb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-iverify.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-iverify
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-iverify.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 51a51b43-322a-020d-becc-2446b24d834c
---

# Set up iVerify Enterprise Mobile Threat Defense with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the iVerify Enterprise platform with Intune.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Before you begin

Before starting the process of integrating iVerify Enterprise with Intune, make sure you have the following configurations:

- **Microsoft Intune Plan 1 subscription**
- **Microsoft Entra admin credentials**to grant the following permissions:
    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- **Admin credentials** to access the iVerify Admin Console

## iVerify Enterprise app authorization

The iVerify Enterprise app authorization process consists of the following steps:

1. Sign in to the **iVerify Enterprise Admin Console**.
2. Navigate to **Integrations** and select **Microsoft Intune Mobile Threat Defense**.
3. When prompted, choose **Accept** to authorize the iVerify MTD app to communicate with Intune and Microsoft Entra ID.
4. Once authorization is complete, configure device policies within the **iVerify Enterprise Admin Console** to define and manage device threat levels across your fleet.

## To set up iVerify Enterprise integration

For step-by-step setup guidance, see [Connecting iVerify Enterprise with Microsoft Intune](https://edr.iverify.io/docs/iverify-portal-guide/Integrations/intune-mtd) in the iVerify documentation.

Note

You'll need to sign in with your iVerify Admin Console credentials to view the documentation.