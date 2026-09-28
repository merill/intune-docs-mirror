---
layout: Conceptual
title: Sample queries for application management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-application-management-configuration-manager
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
description: Sample queries that show how to join the most common application management views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 457d7871-c6de-9876-b183-f6f0adda8b4d
document_version_independent_id: 4ad0c9a8-eb92-e8c8-7e9d-f7e038a143fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-application-management-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-application-management-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-application-management-configuration-manager.md
cmProducts: []
platformId: 3f8b633f-c63d-df14-ca2f-c53286c08c10
---

# Sample queries for application management - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join the most common application management views to other views.

## Joining package and program deployment and collection views

The following query lists all package and program deployments by advertisement ID, advertisement name, and the collection that was targeted for the deployment. The **v\_Advertisement** view is joined to the **v\_Collection** view by using the **AdvertisementID** column.

```sql
    SELECT ADV.AdvertisementID, ADV.AdvertisementName, 
    COL.CollectionID, COL.Name as CollectionName 
    FROM v_Advertisement ADV INNER JOIN v_Collection COL 
    ON ADV.CollectionID = COL.CollectionID 
    ORDER BY ADV.AdvertisementID 
```