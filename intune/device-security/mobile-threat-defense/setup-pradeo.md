---
layout: Conceptual
title: Set up Pradeo Mobile Threat Defense to integrate with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-pradeo
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
description: How to set up the Pradeo Mobile Threat Protection solution with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 11b3ba08-8215-9f1c-df0f-3fc396f6acb1
document_version_independent_id: 11b3ba08-8215-9f1c-df0f-3fc396f6acb1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-pradeo.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-pradeo
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-pradeo.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 3599aa49-dd98-7f37-ff5d-afac0fb170c7
---

# Set up Pradeo Mobile Threat Defense to integrate with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the Pradeo Mobile Threat Defense solution with Intune.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Before you begin

Note

The following steps are to be completed in the [Pradeo Security console](https://pradeo-security.com/).

The process of integrating Pradeo with Intune requires the following subscriptions and account permissions:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra credentials to grant the following permissions:
    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin credentials to access Pradeo Security console.

### Pradeo app authorization

The Pradeo app authorization process follows:

- Allow the Pradeo service to communicate information related to device health state back to Intune.
- Pradeo syncs with Microsoft Entra Enrollment Group membership to populate its device's database.
- Allow Pradeo admin console to use Microsoft Entra single sign-on (SSO).
- Allow the Pradeo app to sign in using Microsoft Entra SSO.

## To set up Pradeo integration

1. Go to [Pradeo Security console](https://pradeo-security.com/) and sign in with your credentials.
2. Choose **Administration - Enterprise Mobility Management** from the menu.
3. Choose the **Intune logo**.
4. In the **EMM (Enterprise mobility management) - Intune** window, under **Step 1**, choose the **Pradeo Connector** button.

    ![Screenshot of the Pradeo EMM Intune window](media/setup-pradeo/pradeo_setup.png)
5. In the Microsoft Intune connection window, enter your Intune credentials.
6. The Pradeo web page reopens. Under **Step 2**, choose the **Pradeo Device Health** button.
7. In the Pradeo-Intune Connector window, select **Accept**.
8. In the Pradeo device API connector window, select **Accept**.
9. The Pradeo web page reopens. Under **Step 3**, choose the **Connect to Microsoft** button.
10. In the Microsoft Intune authentication window, enter your Intune credentials.
11. When the message **Successful Integration** appears, integration is complete.