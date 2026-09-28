---
layout: Conceptual
title: CIDetectInfo Structure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure
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
description: Learn how the CIDetectInfo structure contains identity information for baseline configuration item detection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a3f74e49-539c-ce5a-8215-6eefb6391fbc
document_version_independent_id: 4c860605-a5cd-5d36-c8a8-c3c4f5763e08
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure.md
cmProducts: []
platformId: 7806ff4c-7fa2-3efa-9be2-45787728ff3f
---

# CIDetectInfo Structure - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CIDetectInfo` structure contains identity information for baseline configuration item detection.

## Syntax

```
struct CIDetectInfo
{
      LPWSTR szCIID;
      LPWSTR szVersion;
};
```

## Members

szCIID ID of the configuration item.

szVersion Version of the configuration item.