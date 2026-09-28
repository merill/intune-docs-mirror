---
layout: Conceptual
title: Set up CrowdStrike Falcon for Mobile integration with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-crowdstrike-falcon
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
description: How to set up CrowdStrike Falcon Threat Defense with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2025-02-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 7ebb64ff-babb-efbe-09fb-1dc6a3b073d3
document_version_independent_id: 7ebb64ff-babb-efbe-09fb-1dc6a3b073d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-crowdstrike-falcon.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-crowdstrike-falcon
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-crowdstrike-falcon.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 28ddd8f4-6959-5beb-2f92-0b5195770434
---

# Set up CrowdStrike Falcon for Mobile integration with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the CrowdStrike Falcon for Mobile solution with Intune.

Note

This Mobile Threat Defense vendor isn't supported for unenrolled devices.

## Before you begin

The instructions in this article are done in the [CrowdStrike Falcon for Mobile console](https://falcon.crowdstrike.com).

Before starting the process of integrating CrowdStrike Falcon with Intune, make sure you have the following configurations:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra admin credentials to grant the following permissions:

    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin credentials to access the CrowdStrike Falcon for Mobile console.

### CrowdStrike Falcon app authorization

The CrowdStrike Falcon app authorization process consists of the following steps:

- Allow the CrowdStrike Falcon for Mobile service to communicate information related to device health state back to Intune.
- CrowdStrike Falcon syncs with Microsoft Entra Enrollment Group membership to populate its device's database.
- Allow the CrowdStrike Falcon for Mobile console to use Microsoft Entra single sign-on (SSO).
- Allow the CrowdStrike Falcon app to sign in using Microsoft Entra SSO.

## Set up CrowdStrike Falcon for Mobile integration

CrowdStrike documents the integration steps at [Integrating Falcon for Mobile with Microsoft Intune for remediation actions](https://falcon.crowdstrike.com/documentation/page/odf8977b/integrating-falcon-for-mobile-with-microsoft-intune-for-remediation-actions). You must sign in with your CrowdStrike credentials before you can access this content.