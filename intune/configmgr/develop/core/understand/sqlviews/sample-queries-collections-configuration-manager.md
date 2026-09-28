---
layout: Conceptual
title: Sample queries for collections - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-collections-configuration-manager
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
description: Sample queries that show how to join some of the most commonly used collection views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 60e2cf3f-e806-be17-0d07-11537aa40df3
document_version_independent_id: cfa72cad-359f-211c-e95f-28ccd1cf5430
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-collections-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-collections-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-collections-configuration-manager.md
cmProducts: []
platformId: afaab325-ef87-5181-0ff7-feb65cfd9701
---

# Sample queries for collections - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join some of the most commonly used collection views to other views.

## Joining collection views

The following query lists the resources in the Configuration Manager hierarchy that are in a collection, the assigned site for client computers, the collection ID, collection name, and the last time the collection was refreshed. The **v\_FullCollectionMembership** view is joined to the **v\_Collection** view by using the **CollectionID** column. The query results are sorted by resource name and then by collection ID.

```sql
    SELECT FCM.Name, FCM.SiteCode, FCM.CollectionID, 
    ��COL.Name, COL.LastRefreshTime 
    FROM v_FullCollectionMembership FCM INNER JOIN v_Collection COL 
    ��ON FCM.CollectionID = COL.CollectionID 
    ORDER BY FCM.Name, FCM.CollectionID 
```

## Joining collection and resource views

The following query lists all of the discovered resources that do not have a Configuration Manager client installed. The query lists the domain, computer name, and all discovered IP addresses using data by joining three views. The **v\_CM\_RES\_COLL\_SMS00001** collection view is joined to the **v\_R\_System** and **v\_RA\_IPAddresses** discovery views by using the **ResourceID** column.

```sql
    SELECT SYS.Resource_Domain_OR_Workgr0, COLL1.Name, 
    ��SYSIP.IP_Addresses0 
    FROM v_CM_RES_COLL_SMS00001 COLL1 
    ��INNER JOIN v_R_System SYS 
    ��ON COLL1.ResourceID = SYS.ResourceID 
    ��INNER JOIN v_RA_System_IPAddresses SYSIP 
    ��ON COLL1.ResourceID = SYSIP.ResourceID 
    WHERE COLL1.IsClient = 0 
    ORDER BY SYS.Resource_Domain_OR_Workgr0, COLL1.Name 
```

## Joining collection and deployment views

The following query lists all of the resources in the Configuration Manager hierarchy that have been targeted for an advertisement, as well as the source site code, advertisement ID and advertisement name, program name, and target collection name, and then it sorts the data by the name of the resource. The **v\_FullCollectionMembership** collection view is joined to the **v\_Advertisement** software distribution view and **v\_Collection** collection view by using the **CollectionID** column.

```sql
    SELECT FCM.Name AS ResourceName, FCM.ResourceID, 
    ��ADV.SourceSite, ADV.AdvertisementID, ADV.AdvertisementName, 
    ��ADV.ProgramName, COL.Name AS CollectionName 
    FROM v_FullCollectionMembership FCM INNER JOIN v_Advertisement ADV 
    ��ON FCM.CollectionID = ADV.CollectionID INNER JOIN 
    ��v_Collection COL ON FCM.CollectionID = COL.CollectionID 
    ORDER BY FCM.Name 
```