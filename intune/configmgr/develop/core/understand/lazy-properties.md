---
layout: Conceptual
title: SMS object lazy properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/lazy-properties
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
description: Learn how to use lazy properties, which are properties that exist and contain data, but the data isn't available through the SMS Administrator console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 052469f4-6a39-10c3-6c31-313570582425
document_version_independent_id: 867ab68b-a4fa-49da-e6ff-a63fdd9c5c29
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/lazy-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/lazy-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/lazy-properties.md
cmProducts: []
platformId: 8e4281ba-bd53-0e0d-c47f-4e3fdcf88818
---

# SMS object lazy properties - Configuration Manager | Microsoft Learn

A few SMS object properties are described as lazy. This means that the property exists and contains data, but the data isn't available through the SMS Administrator console. In practical terms, the property isn't visible in Query Builder.

The lazy properties generally contain data that is useless when displayed in the SMS Administrator console. For example, the **Icon[ ]** property in **SMS\_PDF\_Package** is an array of icon data that appears in the SMS Administrator console as a large amount of uninterpretable numeric data.

Lazy properties can be accessed programmatically if you have an application that requires the data that they store. The data can only be retrieved by explicitly calling **GetInstance** on the object.