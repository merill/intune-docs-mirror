---
layout: Conceptual
title: ICIINFO Interface - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface
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
description: ICIINFO can represent a configuration item which has been downloaded and stored by the Desired Configuration Management client or a baseline configuration item in a Desired Configuration Management Agent job in the client data store.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b935d693-e8e6-36f0-c85d-e5ec372ffb2b
document_version_independent_id: 1809d8e2-3923-3a3b-85ef-602a967116fb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface.md
cmProducts: []
platformId: 67d16250-9b70-c86f-757e-11cab5529ab2
---

# ICIINFO Interface - Configuration Manager | Microsoft Learn

The `ICIINFO` interface, in Configuration Manager, can represent the properties of a configuration item which has been downloaded and stored by the Desired Configuration Management client or the properties of a baseline configuration item in a Desired Configuration Management Agent job in the client data store. In both cases, the configuration item is either a (top level/root) baseline or a Software Updates configuration item.

The interface inherits from `IUnknown`.