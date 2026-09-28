---
layout: Conceptual
title: Reporting views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/reporting-views-configuration-manager
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
description: Information about built-in and user-created reports.
ms.date: 2021-11-22T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e40a3bfe-0667-2af2-9528-911a1aa62314
document_version_independent_id: 0f818e84-f3f8-7276-7372-427d5123028b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/reporting-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/reporting-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/reporting-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: c7143a83-b4ba-d79c-1011-ff11bb67c231
---

# Reporting views - Configuration Manager | Microsoft Learn

Reporting in Configuration Manager uses the SQL Server Reporting Services (SSRS) to store and generate reports. For this reason, information about built-in and user-created reports is stored in the SQL Server Reporting Services database and not the Configuration Manager database.

You can run the following query against your Reporting Services database to retrieve a list of the built-in and user-created reports at your site.

```sql
    SELECT *
    FROM <report server name>.dbo.Catalog
    ORDER BY Name
```

For more information about the built-in reports supplied with Configuration Manager, see [List of reports in Configuration Manager](../../../../core/servers/manage/list-of-reports).