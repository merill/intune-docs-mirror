---
layout: Conceptual
title: Set up Trustd Mobile Threat Defense integration with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-trustd-mobile
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: Brenduns
ms.author: brenduns
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: How to set up Trustd Mobile Threat Defense with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2026-06-24T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: 53a540c7-bcfd-b627-caae-95ab228b61cf
document_version_independent_id: 53a540c7-bcfd-b627-caae-95ab228b61cf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-trustd-mobile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-trustd-mobile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-trustd-mobile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: e85be933-f97c-5ca3-d062-23f8f3e50c56
---

# Set up Trustd Mobile Threat Defense integration with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the Trustd Mobile solution with Intune. The instructions in this article are performed in the [Trustd Mobile console](https://control.traced.app/devices/zero-trust/intune).

## Before you begin

Before starting the process of integrating Trustd Mobile with Intune, make sure you have the following configurations:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra admin credentials to grant the following permissions:
    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin credentials to access the Trustd Mobile console

## Trustd Mobile app authorization

The Trustd Mobile app authorization process consists of the following steps:

1. Go to the [Trustd Mobile console](https://control.traced.app/devices/zero-trust/intune) and sign in with your credentials.
2. Choose **Settings** from the top bar.
3. Choose **Integrations** from the left bar.
4. Under **Microsoft Intune**, select **Authorise now**.
5. Authenticate to Microsoft and add the Trustd Mobile Intune Connector app.

Important

To perform the Trustd Mobile integration setup, you must sign in with a Microsoft Entra user who has the Global Administrator role. This one-time setup operation uses the Global Administrator rights to grant permission in your organization for the Trustd Mobile apps to communicate with Intune.

## Set up Trustd Mobile integration

For step-by-step setup guidance, see [Microsoft Intune – Zero Trust Conditional Access](https://traced.app/getting-started-guide-unmanaged-customer/#step12) in the Trustd Mobile documentation.