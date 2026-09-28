---
layout: Conceptual
title: CIEvalState Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration
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
description: In Configuration Manager, the CIEvalState enumeration is used by the ICIINFO Interface.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 88ee39a0-9165-fec2-372e-fe1b769529bd
document_version_independent_id: 7f686336-e769-738c-4c17-402f61f95d8d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration.md
cmProducts: []
platformId: fbaccb2a-3abd-a587-0ddb-21930a0e0d26
---

# CIEvalState Enumeration - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CIEvalState` enumeration defines configuration item evaluation states. This enumeration is used by the [ICIINFO Interface](iciinfo-interface).

## Syntax

```
typedef enum tagCIEvalState
{
  ciIdle = 0,
  ciEvaluating
} CIEvalState;
```

## Elements

ciIdle Configuration item is idle.

ciEvaluating Configuration item is being evaluated.