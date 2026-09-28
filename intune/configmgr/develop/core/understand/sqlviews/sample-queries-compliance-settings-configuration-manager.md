---
layout: Conceptual
title: Sample queries for compliance settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-compliance-settings-configuration-manager
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
description: Sample queries that show how to join compliance settings views to each other and to views from other view categories.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 487a9587-702f-ab98-a65b-4f7980bb5b0a
document_version_independent_id: c0c3cad7-4307-b49d-c955-c46f4d39c9a6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-compliance-settings-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-compliance-settings-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-compliance-settings-configuration-manager.md
cmProducts: []
platformId: a1cff776-69a2-7589-c0e5-bd52dc995e19
---

# Sample queries for compliance settings - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join Configuration Manager compliance settings views to each other and to views from other view categories. Compliance settings views will most often use the **CI\_ID**, **AssignmentID**, and **ResourceID** columns when joining to other views.

## Joining compliance settings and software updates Views

The following query retrieves all configuration items with the type of Software Updates (**CIType\_ID** = 1) or Software Updates Bundle (**CIType\_ID** = 8) that have been deployed to clients (**IsDeployed** =1), listing the article ID, software update name, and software update description. The results are sorted in descending order by article ID. The query joins the **v\_ConfigurationItems** and **v\_CITypes** compliance settings views by using the **CIType\_ID** column, joins the **v\_ConfigurationItems** and **v\_LocalizedCIProperties** compliance settings views by using the **CI\_ID** column, and joins the **v\_ConfigurationItems** view with the **v\_UpdateInfo** software updates view by using the **CI\_ID** column.

```sql
    SELECT v_UpdateInfo.ArticleID, v_LocalizedCIProperties.DisplayName, v_LocalizedCIProperties.Description 
    FROM v_ConfigurationItems INNER JOIN v_CITypes ON v_ConfigurationItems.CIType_ID = v_CITypes.CIType_ID 
    ��INNER JOIN v_LocalizedCIProperties ON v_ConfigurationItems.CI_ID = v_LocalizedCIProperties.CI_ID 
    ��INNER JOIN v_UpdateInfo ON v_ConfigurationItems.CI_ID = v_UpdateInfo.CI_ID 
    WHERE (v_CITypes.CIType_ID = 1 OR v_CITypes.CIType_ID = 8) AND (v_ConfigurationItems.IsDeployed = 1) 
    ORDER BY v_UpdateInfo.ArticleID DESC 
```

## Joining compliance settings, status, and discovery views

The following query retrieves the configuration baselines that have been evaluated on clients, the configuration baseline description, a list of the clients that have a non-compliant state for the configuration baseline, the IP address for the client, and the date and time for the last compliance state message. The results are sorted by configuration baseline name and then computer name. The query joins the **v\_CIComplianceStatusDetail** status message with the **v\_RA\_System\_IPAddresses** discovery view by using the **ResourceID** column, and it joins the **v\_CI\_ComplianceStatusDetail** view with the **v\_LocalizedCIProperties** compliance settings view by using the **CI\_ID** column. A filter could be added to the query to specify the client computer or the configuration baseline to reduce the query results.

```sql
    SELECT DISTINCT v_LocalizedCIProperties.DisplayName AS [Baseline Name], 
    ��v_LocalizedCIProperties.Description AS [Baseline Description], 
    ��v_CIComplianceStatusDetail.Netbios_Name0 AS [Computer Name], 
    ��v_RA_System_IPAddresses.IP_Addresses0 AS [IP Address], v_CIComplianceStatusDetail.RuleSeverity, 
    ��v_CIComplianceStatusDetail.LastComplianceMessageTime AS [Last Compliance Message] 
    FROM�v_CIComplianceStatusDetail INNER JOIN v_RA_System_IPAddresses ON 
    ��v_CIComplianceStatusDetail.ResourceID = v_RA_System_IPAddresses.ResourceID 
    ��INNER JOIN v_LocalizedCIProperties ON v_CIComplianceStatusDetail.CI_ID = v_LocalizedCIProperties.CI_ID 
    ORDER BY [Baseline Name], [Computer Name] 
```

## Joining compliance settings, status, and assignment views

The following query retrieves the names of computers that have been targeted for an assignment, the configuration item name assigned to the computer, the compliance state for the item, the assignment name that contains the item, and the target collection for the assignment. The results are sorted by the compliance state, assigned configuration item, and then the computer name. The query joins the **v\_CICurrentComplianceStatus** status view to the **v\_CIAssignmentToCI** compliance settings view by using the **CI\_ID** column; joins the **v\_CIAssignment** and **v\_CIAssignmentToCI** compliance settings views by using the **AssignmentID** column; joins the **v\_LocalizedCIProperties** compliance settings view to the **v\_CICurrentComplianceStatus** view by using the **CI\_ID** column; joins the **v\_StateNames** and **v\_CICurrentComplianceStatus** status views by using the **StateID** and **ComplianceState** columns, respectively; and joins the **v\_R\_System** discovery view to the **v\_CICurrentComplianceStatus** view by using the **ResourceID** column. The retrieved information is filtered by the topic type of 401, which includes state messages for configuration item compliance.

```sql
    SELECT v_R_System.Netbios_Name0 AS [Computer Name], v_LocalizedCIProperties.DisplayName AS [Assigned Item], 
    ��v_StateNames.StateName, v_CIAssignment.AssignmentName, v_CIAssignment.CollectionID 
    FROM v_CICurrentComplianceStatus 
    ��INNER JOIN v_CIAssignmentToCI ON v_CICurrentComplianceStatus.CI_ID = v_CIAssignmentToCI.CI_ID 
    ��INNER JOIN v_CIAssignment ON v_CIAssignmentToCI.AssignmentID = v_CIAssignment.AssignmentID 
    ��INNER JOIN v_LocalizedCIProperties ON v_CICurrentComplianceStatus.CI_ID = v_LocalizedCIProperties.CI_ID 
    ��INNER JOIN v_StateNames ON v_CICurrentComplianceStatus.ComplianceState = v_StateNames.StateID 
    ��INNER JOIN v_R_System ON v_CICurrentComplianceStatus.ResourceID = v_R_System.ResourceID 
    WHERE (v_StateNames.TopicType = 401) 
    ORDER BY v_StateNames.StateName, [Assigned Item], [Computer Name] 
```