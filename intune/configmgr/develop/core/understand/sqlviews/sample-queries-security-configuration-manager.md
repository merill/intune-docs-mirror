---
layout: Conceptual
title: Sample queries for security - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-security-configuration-manager
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
description: Sample queries that show how to join security views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e34e06ec-cc03-f1f3-3160-756084731aec
document_version_independent_id: 489c93ed-ce32-53a6-b58d-f5c0f14c16a2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-security-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-security-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-security-configuration-manager.md
cmProducts: []
platformId: 5c695d78-c2a0-9f30-7a7a-c34cce7bcb8b
---

# Sample queries for security - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join security views to other views.

## Joining security views

The following query lists the user name, object name, and class permission name that the user has on the secured object. The **v\_SecuredObject** view is joined to the **v\_UserClassPermNames** view by using the **ObjectKey** column.

```sql
    SELECT UCP.UserName, SO.ObjectName, UCP.PermissionName 
    FROM v_SecuredObject SO INNER JOIN v_UserClassPermNames UCP 
    ON SO.ObjectKey = UCP.ObjectKey 
    ORDER BY UCP.UserName, SO.ObjectName, UCP.PermissionName 
```

## Joining security and collection views

The following query lists all collections, by collection ID and collection name, the user name, and the instance permissions for that collection. The **v\_Collection** collection view is joined to the **v\_UserInstancePermNames** security view by using the **CollectionID** column and the **InstanceKey** column, respectively.

```sql
    SELECT COL.CollectionID, COL.Name AS CollectionName, UIP.UserName, 
    UIP.PermissionName 
    FROM v_Collection COL INNER JOIN v_UserInstancePermNames UIP 
    ON COL.CollectionID = UIP.InstanceKey 
    ORDER BY COL.CollectionID 
```

The output from the preceding query will list all instance permissions for individual collections. If a user has class permissions for the collections object (which includes all instances), another query will need to be run to get all of the permissions for users on the collections object. (An object key of 1 refers to the collection object.)

The following query can be run from the **v\_UserClassPermNames** view to list all user class permissions for the collections object.

```sql
    SELECT UserName, PermissionName 
    FROM v_UserClassPermNames 
    WHERE ObjectKey = 1 
```

When using the two preceding queries together, a list of user permissions for all collection classes and instances can be obtained.