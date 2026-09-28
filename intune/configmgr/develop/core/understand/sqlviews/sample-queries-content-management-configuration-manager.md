---
layout: Conceptual
title: Sample queries for content management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-content-management-configuration-manager
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
description: Sample queries that show how to join the most common content management views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 050df059-fb2e-c92b-669b-ae3596295745
document_version_independent_id: b871bbaa-8608-8b90-162c-4ae88e353c36
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-content-management-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-content-management-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-content-management-configuration-manager.md
cmProducts: []
platformId: 3fbd0c6d-45f2-49a5-bc82-1e5525e1f7aa
---

# Sample queries for content management - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join the most common content management views to other views.

## Joining software distribution and package status views

The following query lists all packages by package ID and package name, the current status of each package, the Network Abstraction Layer (NAL) path for the distribution point, and the last time the package was refreshed on the distribution point. The **v\_Package** view is joined to the **v\_PackageStatusDetailSumm** status view and **v\_DistributionPoint** software distribution view by using the **PackageID** columns.

```sql
    SELECT PCK.PackageID, PCK.Name as PackageName, PSD.Targeted, 
    PSD.Installed, PSD.Retrying, PSD.Failed, DP.ServerNALPath, 
    DP.LastRefreshTime 
    FROM v_Package PCK INNER JOIN v_PackageStatusDetailSumm PSD 
    ON PCK.PackageID = PSD.PackageID INNER JOIN v_DistributionPoint DP 
    ON PCK.PackageID = DP.PackageID 
    ORDER BY PCK.PackageID 
```