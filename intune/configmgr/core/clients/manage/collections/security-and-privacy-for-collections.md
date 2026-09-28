---
layout: Conceptual
title: Collections security and privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/security-and-privacy-for-collections
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Recommendations for security and privacy with collections in Configuration Manager.
ms.date: 2021-05-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 5f88838d-8a1b-933a-9223-549fc2e36152
document_version_independent_id: 0e2e1f9e-7a5d-8446-3848-550f51471f99
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/collections/security-and-privacy-for-collections.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/collections/security-and-privacy-for-collections
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/collections/security-and-privacy-for-collections.md
cmProducts: []
platformId: 170881c8-2048-155e-a5c2-659a858e8629
---

# Collections security and privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article contains security recommendations and privacy information for collections in Configuration Manager.

## Security recommendations

When you export or import a collection by using a managed object format (MOF) file that's saved to a network location, secure the location and the network channel. Restrict who can access the network folder. Use Server Message Block (SMB) signing or Internet Protocol security (IPsec) between the network location and the site server. These mechanisms help prevent an attacker from tampering with the exported collection data. Use IPsec to encrypt the data on the network to prevent information disclosure.

## Security issues

Collections have the following security issues:

- If you use collection variables, local administrators can read potentially sensitive information. Collection variables are only used when you deploy an OS. For more information, see [Collection and device variables](../../../../osd/understand/using-task-sequence-variables#bkmk_set-coll-var).

## Privacy information

There's no privacy information specifically for collections in Configuration Manager. Collections are containers for resources, such as users and devices. Collection membership often depends on the information that Configuration Manager collects during standard operation.

Configuration Manager can collect resource information from discovery or inventory. Using this information, you can configure a collection to contain the devices that meet your specified criteria. Collections might also be based on the current status information for client management operations. For example, deploying software or checking for compliance. Along with query-based collections, you can also directly add resources to collections.