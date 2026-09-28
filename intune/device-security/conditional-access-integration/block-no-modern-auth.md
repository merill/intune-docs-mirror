---
layout: Conceptual
title: Block Apps with No Modern Authentication on Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/block-no-modern-auth
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- sub-device-compliance
ms.reviewer: beflamm
ms.subservice: protect
description: Learn about applications and modern authentication (MSAL) using Microsoft Intune.
ms.date: 2024-03-28T00:00:00.0000000Z
ms.topic: article
locale: en-us
document_id: 40f57625-acdd-8750-9496-9dae360d8dd1
document_version_independent_id: 40f57625-acdd-8750-9496-9dae360d8dd1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/conditional-access-integration/block-no-modern-auth.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/conditional-access-integration/block-no-modern-auth
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/conditional-access-integration/block-no-modern-auth.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5f286262-a4cb-47f4-92d3-dc24f172492b
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e31b9be-b6e9-4221-a20b-d1460dbd5dfa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/90571f66-8410-4272-8117-79ce87fc2dcc
- https://authoring-docs-microsoft.poolparty.biz/devrel/8d63a4c4-4889-43b4-a98e-8e50dbfdb083
platformId: 967d3ee6-3848-7d0e-ba0e-d587f0f55f11
---

# Block Apps with No Modern Authentication on Intune - Microsoft Intune | Microsoft Learn

App-based Conditional Access with app protection policies rely on applications using [modern authentication](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), which is an implementation of OAuth2. Most current Office mobile and desktop applications use modern authentication. However, there are third-party apps and older Office apps that use other authentication methods, like basic authentication and forms-based authentication.

## Block access to apps

To block access to apps that don't use modern authentication, use Intune app protection policies to implement Conditional Access. For more information, see [App-based Conditional Access with Intune](app-based-policies).

## Additional information

For more information about Microsoft Entra Conditional Access, see the following topics:

- [What is Conditional Access in Microsoft Entra ID?](/en-us/entra/identity/conditional-access/overview)
- [How app-based Conditional Access works](app-based-policies#how-app-based-conditional-access-works)