---
layout: Conceptual
title: AppDeploymentTypeData Structure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypedata-structure
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
description: The AppDeploymentTypeData structure contains detection results for a set of deployment types.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1d6e4891-9465-88d4-04b7-08b491dce92d
document_version_independent_id: 4cee85a1-c9b5-47d6-85dd-4604be70e05f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypedata-structure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/appdeploymenttypedata-structure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypedata-structure.md
cmProducts: []
platformId: 74741df4-5cc7-1c1e-62df-7892d29dbd01
---

# AppDeploymentTypeData Structure - Configuration Manager | Microsoft Learn

In Configuration Manager, the `AppDeploymentTypeData` structure contains detection results for a set of deployment types.

## Syntax

```
typedef struct tagAppDeploymentTypeData
{
    DWORD cbSize;
    DWORD dwCount;
    PAppDeploymentTypeItem pData;
}AppDeploymentTypeData;
```

## Members

`cbSize` The size of this structure to indicate version.

`dwCount` The number of discovered items.

`PAppDeploymentTypeItem` An array of discovered items.