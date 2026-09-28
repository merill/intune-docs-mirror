---
layout: Conceptual
title: Manage access to Exchange without device management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/manage-exchange-access
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-device-compliance
ms.reviewer: demerson
ms.subservice: protect
description: Use Microsoft Intune to give employees access to their Microsoft 365 Exchange Online email without setting up a device management system.
ms.date: 2024-11-07T00:00:00.0000000Z
ms.topic: archived
locale: en-us
document_id: 258e33b6-8f5c-115a-e2e9-5830f3698aef
document_version_independent_id: 258e33b6-8f5c-115a-e2e9-5830f3698aef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/conditional-access-integration/manage-exchange-access.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/conditional-access-integration/manage-exchange-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/conditional-access-integration/manage-exchange-access.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cf9b82c5-b6dc-45f3-b005-b1bc5fc03bea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0c85d34e-bfd2-4466-957c-f0b61e9692df
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 56d7399e-198e-8f2e-4ec6-bdeb273ccaa2
---

# Manage access to Exchange without device management - Microsoft Intune | Microsoft Learn

When you use Microsoft Intune, you can still manage employee access to their work email through Microsoft 365 Exchange Online without the overhead of enrolling their devices. This limited access through Exchange Online for unenrolled devices can be accomplished using app-based Conditional Access policies.

To complete the necessary steps, confirm you have licenses for Microsoft 365, or Microsoft Entra ID P1 and Intune. Employees need to have a [supported iOS/iPadOS or Android device](../../fundamentals/ref-supported-platforms).

If you decide to set up a device management system, you can, as this type of app protection works independently of device management.

## Action plan

1. [Learn about Conditional Access](overview).
2. [Learn about app-based Conditional Access](app-based-policies).
3. [Set up app-based Conditional Access policies for Exchange Online](create-app-based-policy).
4. [Block apps that can't be managed](block-no-modern-auth). Specifically, block apps that don't use the Microsoft Authentication Library (MSAL).
5. (Optional) [Set up app-based Conditional Access policies for SharePoint Online](create-app-based-policy). These policies block access to your company data from apps that can't be managed and secured. The policies also limit access through SharePoint mobile.

## What to tell employees and students

- Ask your employees and students to download and install Microsoft Outlook or Microsoft SharePoint for iOS/iPadOS from the Apple App Store or for Android from the Google Play Store.
- If you block access to apps that don't use modern authentication, let the employees and students know of this restriction.