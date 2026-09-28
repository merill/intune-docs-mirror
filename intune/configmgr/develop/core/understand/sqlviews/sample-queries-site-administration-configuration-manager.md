---
layout: Conceptual
title: Sample queries for site administration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-site-administration-configuration-manager
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
description: Sample queries that show how to join site administration views to other views to retrieve specific data.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: caa30b13-b5f0-b4c7-f582-9af9278dc3ea
document_version_independent_id: 06510180-8cb4-0230-db20-983eba7141a2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-site-administration-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-site-administration-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-site-administration-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: fd13d0f2-1f82-295c-1cf8-b77750b805bd
---

# Sample queries for site administration - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how the Configuration Manager site administration views can be joined to other views to retrieve specific data.

## Joining site administration views

The following sample query demonstrates how to join a site view to another site view. This query lists the boundaries for each site in the Configuration Manager hierarchy, the type of boundary, the boundary value, whether the connection is fast or slow, and the boundary description. The **v\_Site** and **v\_BoundaryInfo** site views are joined by using the **SiteCode** column. The query results are sorted by site code, boundary type, and then value. The CASE function is used to take a numeric value for boundary type and connection speed and to provide friendly names based on the value.

```sql
    SELECT v_Site.SiteCode, v_Site.ServerName, 
    ��CASE v_BoundaryInfo.BoundaryType 
    ����WHEN 0 THEN 'IP subnet' 
    ����WHEN 1 THEN 'Active Directory site' 
    ����WHEN 2 THEN 'IPv6 Prefix' 
    ����WHEN 3 THEN 'IP address range' 
    ��END AS [Boundary Type], v_BoundaryInfo.Value, 
    ��CASE v_BoundaryInfo.BoundaryFlags 
    ����WHEN 0 THEN 'Fast' 
    ����WHEN 1 THEN 'Slow' 
    END AS Connection, v_BoundaryInfo.DisplayName AS Description 
    FROM v_BoundaryInfo INNER JOIN v_Site ON v_BoundaryInfo.SiteCode = v_Site.SiteCode 
    ORDER BY v_Site.SiteCode, [Boundary Type], v_BoundaryInfo.Value
```