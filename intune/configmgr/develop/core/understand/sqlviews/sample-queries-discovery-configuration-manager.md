---
layout: Conceptual
title: Sample queries for discovery - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-discovery-configuration-manager
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
description: Sample queries that show how to join discovery views to each other and views from other view categories.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: aca16d18-8709-c64a-a803-34121eae5fb7
document_version_independent_id: 2d75c299-3644-acf4-20c8-1650fefa1b6f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-discovery-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-discovery-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-discovery-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 13bbab73-fdfd-8d00-3a10-7e95dd82f645
---

# Sample queries for discovery - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join Configuration Manager discovery views to each other and views from other view categories. Discovery views use the **ResourceID** column when joining to other views.

## Joining discovery views

The following query retrieves all resources and their associated IP addresses. The query joins the **v\_R\_System** and **v\_RA\_System\_IPAddresses** discovery views by using the **ResourceID** column.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, SYSIP.IP_Addresses0 
    FROM v_R_System SYS INNER JOIN v_RA_System_IPAddresses SYSIP 
    ��ON SYS.ResourceID = SYSIP.ResourceID 
    ORDER BY SYS.Netbios_Name0 
```

## Joining resource and inventory views

The following query retrieves all resources that have a local fixed disk listed in inventory and displays the NetBIOS name, the free disk space, and sorts the data in ascending order by free disk space. The query joins the **v\_R\_System** discovery view and the **v\_GS\_LOGICAL\_DISK** hardware inventory view by using the **ResourceID** column.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, LD.FreeSpace0 
    FROM v_R_System SYS INNER JOIN v_GS_LOGICAL_DISK LD 
    ��ON SYS.ResourceID = LD.ResourceID 
    WHERE LD.Description0 LIKE 'Local fixed disk' 
    ORDER BY LD.FreeSpace0 
```

## Joining resource and collection views

The following query retrieves all resources in the **All Systems** collection and displays the NetBIOS name, domain name, and associated IP addresses. The query results are sorted by NetBIOS name. The query joins the **v\_R\_System** and **v\_RA\_System\_IPAddresses** discovery views, and joins the **v\_FullCollectionMembership** collection view by using the **ResourceID** column.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, FCM.Domain, SYSIP.IP_Addresses0 
    FROM v_R_System SYS INNER JOIN v_FullCollectionMembership FCM 
    ON SYS.ResourceID = FCM.ResourceID 
    INNER JOIN v_RA_System_IPAddresses SYSIP 
    ON SYS.ResourceID = SYSIP.ResourceID 
    WHERE FCM.CollectionID = 'SMS00001' 
    ORDER BY SYS.Netbios_Name0 
```

## Joining resource, software updates, and status views

The following query retrieves all resources that have performed a scan for software updates, the last scan time, the last scan state, and the Windows Update Agent version on the client. The query joins the **v\_R\_System** discovery view and **v\_UpdateScanStatus** software updates view by using the **ResourceID** column, and it uses LEFT OUTER JOIN between the **v\_UpdateScanStatus** software updates view and **v\_StateNames** status view by using the **LastScanState** and **StateID** columns. The state message topic types are filtered by **TopicType = 501**, which indicates scan-state messages.

Note

The state topic type, state ID, state name, and state description for all Configuration Manager state messages are listed in the **v\_StateNames** view.

```sql
    SELECT DISTINCT v_R_System.Netbios_Name0 AS [Computer Name], 
    ��v_UpdateScanStatus.LastScanTime AS [Last Scan], 
    ��v_UpdateScanStatus.LastWUAVersion AS [WUA Version], 
    ��v_StateNames.StateName AS [Last Scan State] 
    FROM v_UpdateScanStatus INNER JOIN v_R_System ON 
    ��v_UpdateScanStatus.ResourceID = v_R_System.ResourceID LEFT OUTER JOIN 
    ��v_StateNames ON v_UpdateScanStatus.LastScanState = v_StateNames.StateID 
    WHERE (v_StateNames.TopicType = 501) 
```