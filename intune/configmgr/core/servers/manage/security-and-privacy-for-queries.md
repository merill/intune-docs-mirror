---
layout: Conceptual
title: Security and privacy for queries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/security-and-privacy-for-queries
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
description: Understand best practices for security and privacy when you query for information from the site database.
ms.date: 2019-05-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: e5684edd-3a6f-a35f-06ad-912612077c4a
document_version_independent_id: 1f9421e7-e76e-9b52-3294-17c9fb403c3d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/security-and-privacy-for-queries.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/security-and-privacy-for-queries
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/security-and-privacy-for-queries.md
cmProducts: []
platformId: 4dba6a38-92d8-c7f1-48c4-516e62dd62e5
---

# Security and privacy for queries - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Queries in Configuration Manager let you retrieve information from the site database according to criteria that you specify. Configuration Manager collects site database information during standard operation. For example, by using information that's been collected during discovery or inventory, you can configure a query to identify devices that meet specified criteria.

For more information about queries, see [Introduction to queries](introduction-to-queries). For security best practices and privacy information about Configuration Manager operations that collect the data you can retrieve by using queries, see [Security and privacy for Configuration Manager](../../../security/).

## Security best practices for queries

Use this security best practice for queries.

| Security best practice | More information |
| --- | --- |
| When you export or import a query that's saved to a network location, secure the location and the network channel. | Restrict who can access the network folder. Use Server Message Block (SMB) signing or Internet Protocol security (IPsec) between the network location and the site server to prevent an attacker from tampering with the query data before it's imported. |