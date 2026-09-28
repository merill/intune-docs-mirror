---
layout: Conceptual
title: AppDeploymentTypeItem Structure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypeitem-structure
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
description: Learn about the AppDeploymentTypeItem structure that contains detection results for an individual deployment type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5fbfac3b-ae06-9ea9-db35-1d5aa2493995
document_version_independent_id: e021ad51-3e51-76cc-feb0-e3c4c7f4fa7d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypeitem-structure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/appdeploymenttypeitem-structure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypeitem-structure.md
cmProducts: []
platformId: b74b275a-8463-0963-ddc5-19db48a913d8
---

# AppDeploymentTypeItem Structure - Configuration Manager | Microsoft Learn

In Configuration Manager, the `AppDeploymentTypeItem` structure contains detection results for an individual deployment type.

## Syntax

```
typedef struct tagAppDeploymentTypeItem
{
    LPWSTR szId;
    DWORD dwRevision;
    AppDetectState eDetectState;
    DWORD dwErrorCode;
}AppDeploymentTypeItem, *PAppDeploymentTypeItem;
```

## Members

`szId` ID of the deployment item.

`dwRevision` Revision.

`eDetectState` Detect state.

dwErrorCode Error code.