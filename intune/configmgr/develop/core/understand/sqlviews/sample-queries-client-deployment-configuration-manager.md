---
layout: Conceptual
title: Sample queries for client deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-client-deployment-configuration-manager
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
description: Sample queries that show how to join the most common client deployment views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b5b35ee0-3baf-506f-c897-eae96adc5f16
document_version_independent_id: 86d888c7-6a22-9ab6-5ab5-b3342e9305ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-client-deployment-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-client-deployment-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-client-deployment-configuration-manager.md
cmProducts: []
platformId: 26f3acc0-9e37-a7bc-51ff-96975914a374
---

# Sample queries for client deployment - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join the most common client deployment views to other views.

The following sample query demonstrates how to join client deployment views with other views. Client deployment views will most often use the **MachineID** column, which is the same as the **ResourceID** column in other views, and **NetBiosName** column when joining to other views.

## Joining client deployment and discovery views

This query retrieves the NetBIOS name for client computers that have provided client deployment status, the user name, assigned site, time of last state message, and state name. The results are sorted by deployment state and then NetBIOS name. The query joins the **v\_ClientDeploymentState** client deployment view with the **v\_R\_System** discovery view by using the **ResourceID** column, and the **v\_ClientDeployment** view with the **v\_StateNames** status view by using the **LastMessageStateID** and **StateID** columns, respectively. The retrieved information is filtered by the topic type of **800**, which includes only state messages for client deployment.

```sql
    SELECT v_ClientDeploymentState.NetBiosName AS Computer, 
    ��v_R_System.User_Name0 AS [User], 
    ��v_ClientDeploymentState.AssignedSiteCode AS [Assigned Site], 
    ��v_ClientDeploymentState.LastMessageTime AS [Last Message], 
    ��v_StateNames.StateName AS State 
    FROM v_ClientDeploymentState INNER JOIN v_R_System ON 
    ��v_ClientDeploymentState.SMSID = v_R_System.SMS_Unique_Identifier0 INNER JOIN v_StateNames ON 
    ��v_ClientDeploymentState.LastMessageStateID = v_StateNames.StateID 
    WHERE (v_StateNames.TopicType = 800) 
    ORDER BY State, Computer 
```