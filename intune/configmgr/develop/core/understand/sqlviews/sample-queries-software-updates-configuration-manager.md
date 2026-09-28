---
layout: Conceptual
title: Sample queries for software updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-updates-configuration-manager
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
description: Sample queries that show how to join software updates views to each other and to views from other view categories.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 2d8e63f2-f32a-11af-c5c7-868af5ba8c46
document_version_independent_id: 708b6e9b-a654-2352-8cbd-368719f6af7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-updates-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-software-updates-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-updates-configuration-manager.md
cmProducts: []
platformId: 9de8aac2-71df-c3bf-afd8-e744123a5f04
---

# Sample queries for software updates - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join software updates views to each other and to views from other view categories. Software updates views will most often use the **CI\_ID** column when joining to other views.

## Joining software updates, discovery, and status views

The following query retrieves the article ID, bulletin ID, software update title, last enforcement state for the update, the time of the last enforcement check, and the time that the last enforcement state message was sent by the Computer1 client. The results are sorted by state name and then by the last modified date for the software update. The query joins the **v\_UpdateComplianceStatus** status view with the **v\_UpdateInfo** software updates view by using the **CI\_ID** column, the **v\_UpdateComplianceStatus** status view with the **v\_R\_System** discovery view by using the **ResourceID** column, and the **v\_UpdateComplianceStatus** status view with the **v\_StateNames** status view by using the **LastEnforcementStatus** and **StateID** columns, respectively. The retrieved information is filtered by the topic type of 402, which includes state messages for configuration item enforcement, and a computer with the NetBIOS name of Computer1.

```sql
    SELECT v_UpdateInfo.ArticleID, v_UpdateInfo.BulletinID, v_UpdateInfo.Title, 
    ��v_StateNames.StateName, v_UpdateComplianceStatus.LastStatusCheckTime, 
    ��v_UpdateComplianceStatus.LastEnforcementMessageTime 
    FROM v_R_System INNER JOIN v_UpdateComplianceStatus ON 
    ��v_R_System.ResourceID = v_UpdateComplianceStatus.ResourceID INNER JOIN v_UpdateInfo ON 
    ��v_UpdateComplianceStatus.CI_ID = v_UpdateInfo.CI_ID INNER JOIN v_StateNames ON 
    ��v_UpdateComplianceStatus.LastEnforcementMessageID = v_StateNames.StateID 
    WHERE (v_StateNames.TopicType = 402) AND (v_R_System.Netbios_Name0 LIKE 'Computer1') 
    ORDER BY v_StateNames.StateName, v_UpdateInfo.DateLastModified 
```

## Joining software updates and compliance settings views

The following query retrieves the software update deployments, by assignment ID (software update deployment ID) and assignment name (deployment name); the software updates that are contained in the deployment, by article ID, bulletin ID, and software update title; and the target collection for the deployment. The results are sorted by the assignment ID and then by article ID. The query joins the **v\_UpdateInfo** software updates view with the **v\_CIAssignmentToCI** compliance settings view by using the **CI\_ID** column, and it joins the **v\_CIAssignmentToCI** view to the **v\_CIAssignment** compliance settings view by using the **AssignmentID** column.

```sql
    SELECT v_CIAssignment.AssignmentID, v_CIAssignment.AssignmentName, 
    ��v_UpdateInfo.ArticleID, v_UpdateInfo.BulletinID, v_UpdateInfo.Title, 
    ��v_CIAssignment.CollectionName, v_CIAssignment.CollectionID 
    FROM v_UpdateInfo INNER JOIN v_CIAssignmentToCI ON 
    ��v_UpdateInfo.CI_ID = v_CIAssignmentToCI.CI_ID INNER JOIN v_CIAssignment ON 
    ��v_CIAssignmentToCI.AssignmentID = v_CIAssignment.AssignmentID 
    ORDER BY v_CIAssignment.AssignmentID, v_UpdateInfo.ArticleID 
```