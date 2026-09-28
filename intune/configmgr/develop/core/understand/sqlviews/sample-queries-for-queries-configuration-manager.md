---
layout: Conceptual
title: Sample queries for the query view - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-for-queries-configuration-manager
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
description: Sample queries that show how the query view can be joined to a security view.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 1fc50292-df33-1fe3-a7be-8f6ed355728d
document_version_independent_id: 6cd792c6-76fa-72c1-10be-1d4b10db4bf7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-for-queries-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-for-queries-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-for-queries-configuration-manager.md
cmProducts: []
platformId: 52bb5646-dbe1-e375-fa1b-2f5b6c90b65d
---

# Sample queries for the query view - Configuration Manager | Microsoft Learn

The following sample query demonstrates how the query view can be joined to a security view. In most cases, the **v\_Query** view won't be used in reports.

## Joining query and security views

The following query lists the query ID, query name, user name, and instance permissions for the user on the query object. The **v\_Query** view is joined to the **v\_UserInstancePermNames** security view by using the **QueryID** from **v\_Query** and **InstanceKey** from **v\_UserInstancePermNames**. Because there might be other secured objects with the same value as the **InstanceKey** (for example, MCM00001 could be a custom query or a package), the query also filters specifically for query objects by using the WHERE clause and an **ObjectKey** value of 7.

```sql
    SELECT Q.QueryID, Q.Name AS QueryName, UIP.UserName, UIP.PermissionName 
    FROM v_Query Q INNER JOIN v_UserInstancePermNames UIP 
    ON Q.QueryID = UIP.InstanceKey 
    WHERE UIP.ObjectKey = 7 
    ORDER BY Q.Name, UIP.UserName 
```