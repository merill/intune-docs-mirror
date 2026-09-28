---
layout: Conceptual
title: AppContentInfo Structure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appcontentinfo-structure
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
description: The AppContentInfo structure provides information about the application content.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 736bf5a1-2099-27f0-d510-9e7dbe08afd4
document_version_independent_id: 066dfa7c-c4e5-887c-5773-d031d70582e7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/appcontentinfo-structure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/appcontentinfo-structure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/appcontentinfo-structure.md
cmProducts: []
platformId: 91d4d279-bcdd-dab6-578e-79394a33fb4c
---

# AppContentInfo Structure - Configuration Manager | Microsoft Learn

In Configuration Manager, the `AppContentInfo` structure contains information about the application content.

## Syntax

```
struct AppContentInfo
{
    LPCWSTR szContentId;
    LPCWSTR szContentVersion;
    LPCWSTR szLocalPath;
};
```

## Members

`szContentId` The content id.

`szContentVersion` The content version.

`szLocalPath` The local path.