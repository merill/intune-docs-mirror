---
layout: Conceptual
title: Sample queries for endpoint protection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-endpoint-protection-configuration-manager
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
description: Sample queries that show how to join the most common Endpoint Protection views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 90312d49-afc8-eb38-2d66-927a5e6d1c29
document_version_independent_id: 09d5557b-377e-f6a4-edcc-c2cc422d3f94
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-endpoint-protection-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-endpoint-protection-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-endpoint-protection-configuration-manager.md
cmProducts: []
platformId: afa77d1b-8c19-5949-467d-3de67ed78467
---

# Sample queries for endpoint protection - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join the most common Endpoint Protection views to other views.

## Joining endpoint protection and collection views

The following query lists the deployment state of the Endpoint Protection client on all computers by using the **v\_GS\_EPDeploymentState** view. For each computer, it also adds the client name and site code by joining by **ResourceID** to the **v\_ClientCollectionMembers** view.

```sql
    SELECT   v_GS_EPDeploymentState_1.ResourceID, v_ClientCollectionMembers.Name, v_ClientCollectionMembers.SiteCode, 
                     v_GS_EPDeploymentState_1.LastMessageTime, v_GS_EPDeploymentState_1.DeploymentState, v_GS_EPDeploymentState_1.Error, 
                     v_GS_EPDeploymentState_1.ErrorCode
    FROM    v_GS_EPDeploymentState AS v_GS_EPDeploymentState_1 INNER JOIN
            v_ClientCollectionMembers ON v_GS_EPDeploymentState_1.ResourceID = v_ClientCollectionMembers.ResourceID
```