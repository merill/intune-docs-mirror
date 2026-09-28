---
layout: Conceptual
title: Set up Check Point Harmony integration with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-checkpoint-harmony
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
description: How to set up CheckPoint Harmony Mobile Threat Defense (MTD) with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 6cd16854-c98a-114e-1d76-937ff45325d6
document_version_independent_id: 6cd16854-c98a-114e-1d76-937ff45325d6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-checkpoint-harmony.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-checkpoint-harmony
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-checkpoint-harmony.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 34ced151-0e3c-ed7a-e6bf-db6c6d0c9410
---

# Set up Check Point Harmony integration with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the Check Point Harmony Mobile Threat Defense solution with Intune.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Before you begin

The instructions in this article are done in the [Check Point Harmony Mobile console](https://portal.checkpoint.com).

Before starting the process of integrating Check Point Harmony Mobile with Intune, make sure you have the following configurations:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra admin credentials to grant the following permissions:

    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin credentials to access Check Point Harmony Mobile MTD console.

### Harmony Mobile Protect app authorization

The Harmony Mobile Protect app authorization process consists of the following steps:

- Allow the Check Point Harmony Mobile service to communicate information related to device health state back to Intune.
- CheckPoint Harmony Mobile syncs with Microsoft Entra Enrollment Group membership to populate its device's database.
- Allow Check Point Harmony admin console to use Microsoft Entra single sign-on (SSO).
- Allow the Harmony Mobile Protect app to sign in using Microsoft Entra SSO.

## To set up Check Point Harmony Mobile integration

1. Go to [Check Point Harmony Mobile MTD console](https://portal.checkpoint.com) and sign in with your credentials.
2. Select on the **Settings** tab.
3. Choose **Device management**, then **Settings**.
4. Choose **Microsoft Intune** from the **MDM Service** drop-down list.
5. Once you set Microsoft Intune as the MDM Service, the **Microsoft Intune Configuration** window pops up, choose the **Add to my organization** for each device platform: iOS/iPadOS, Android and Windows to authorize Harmony Mobile Protect to communicate with Intune and Microsoft Entra ID.

    Important

    You must add all device platforms to proceed to the next step.
6. Choose **Accept** to authorize the Harmony Mobile Protect app to communicate with Intune and Microsoft Entra.
7. Once you enabled all device platforms, you need to enter the Microsoft Entra security group.
8. Choose **Verify**, once the Microsoft Entra security group is successfully verified, choose **Save**.