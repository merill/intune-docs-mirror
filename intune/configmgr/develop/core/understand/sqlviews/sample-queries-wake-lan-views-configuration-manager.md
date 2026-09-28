---
layout: Conceptual
title: Sample queries for Wake on LAN - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-wake-lan-views-configuration-manager
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
description: Sample queries that show how to join Wake On LAN views to application management, discovery, and compliance settings views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8a6b0e44-9d09-523a-fd62-ec10ce8d49d5
document_version_independent_id: 427a953a-6cd4-a270-d064-c251ff708e38
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-wake-lan-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-wake-lan-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-wake-lan-views-configuration-manager.md
cmProducts: []
platformId: bce87e86-77ad-98c5-e99a-9a8ea8b3bf77
---

# Sample queries for Wake on LAN - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join Wake On LAN views to application management, discovery, and compliance settings views. The Wake On LAN views are most often joined to other views by using the **ObjectID** and **ResourceID** columns, and to other Wake On LAN views by using the **ObjectType** column.

## Joining Wake On LAN, application management, and compliance settings views

The following query retrieves the Configuration Manager object type, the deployment ID or advertisement ID, and the name for all objects that have Wake On LAN enabled. The results are sorted by object type and then by object name. The query joins the **v\_WOLGetSupportedObjects** and **v\_WOLEnabledObjects** Wake On LAN views by using the ObjectType column; joins the **v\_WOLEnabledObjects** view with the **v\_Advertisement** software distribution view by performing a LEFT OUTER JOIN on the **ObjectType** and **AdvertisementID** columns, respectively; and joins the **v\_WOLEnabledObjects** view with the **v\_CIAssignment** desired configuration management view by performing a LEFT OUTER JOIN on the **ObjectType** and **Assignment\_UniqueID** columns, respectively. Using the LEFT OUTER JOIN retrieves all records from the **v\_WOLEnabledObjects** view and only the associated records from the **v\_Advertisement** and **v\_CIAssignment** views.

```sql
    SELECT v_WOLGetSupportedObjects.Name AS [Object Type], 
    v_CIAssignment.AssignmentID AS DeploymentID, v_Advertisement.AdvertisementID 
    ��v_WOLEnabledObjects.ObjectName AS Name 
    FROM v_WOLGetSupportedObjects INNER JOIN v_WOLEnabledObjects ON 
    ��v_WOLGetSupportedObjects.ObjectType = v_WOLEnabledObjects.ObjectType 
    ��LEFT OUTER JOIN v_Advertisement ON 
    ��v_WOLEnabledObjects.ObjectID = v_Advertisement.AdvertisementID 
    ��LEFT OUTER JOIN v_CIAssignment ON 
    ��v_WOLEnabledObjects.ObjectID = v_CIAssignment.Assignment_UniqueID 
    ORDER BY [Object Type], Name 
```

## Joining Wake On LAN and discovery views

The following query retrieves client computers, by NetBIOS name, that have been targeted for an advertisement or deployment with Wake On LAN enabled, as well as the name of the advertisement or deployment, the type of object, and the advertisement ID or deployment ID. The results are sorted by NetBIOS name, object type, and then object ID. The query joins the **v\_WOLTargetedClients** Wake On LAN view with the **v\_R\_System** discovery view by using the **ResourceID** column, joins the **v\_WOLEnabledObjects** and **v\_WOLTargetedClients** Wake On LAN views by using the **ObjectID** column, joins the **v\_WOLGetSupportedObjects** and **v\_WOLEnabledObjects** Wake On LAN views by using the **ObjectType** column.

```sql
    SELECT v_R_System.Netbios_Name0 AS Computer, v_WOLEnabledObjects.ObjectName, 
    ��v_WOLGetSupportedObjects.Name AS ObjectType, v_WOLEnabledObjects.ObjectID 
    FROM v_WOLTargetedClients INNER JOIN v_R_System ON 
    ��v_WOLTargetedClients.ResourceID = v_R_System.ResourceID INNER JOIN v_WOLEnabledObjects ON 
    ��v_WOLTargetedClients.ObjectID = v_WOLEnabledObjects.ObjectID INNER JOIN v_WOLGetSupportedObjects ON 
    ��v_WOLEnabledObjects.ObjectType = v_WOLGetSupportedObjects.ObjectType 
    ORDER BY Computer, v_WOLGetSupportedObjects.ObjectType, v_WOLEnabledObjects.ObjectID 
```