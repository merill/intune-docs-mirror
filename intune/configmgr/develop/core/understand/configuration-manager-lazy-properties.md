---
layout: Conceptual
title: Configuration Manager lazy properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties
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
description: If lazy properties are retrieved during query operations, they have null or zero values.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: b5ec65c6-fe33-90a8-0582-bd770cb8a6c5
document_version_independent_id: d469c7f0-c399-6885-f6d4-b3d110ba94f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-lazy-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-lazy-properties.md
cmProducts: []
platformId: d72c385b-c00a-542b-fce9-0016011ae40b
---

# Configuration Manager lazy properties - Configuration Manager | Microsoft Learn

Some Configuration Manager object properties are relatively inefficient to retrieve. If these properties were retrieved for many instances in a class (as might be done in a query), the response would be considerably delayed. Such properties are considered lazy properties and are not usually retrieved during query operations. However, if these properties are retrieved during a query, they have `null` or zero values, which might not be the actual value of the property for every instance. Therefore, if you want to get the correct value for lazy properties, you must get each instance individually.