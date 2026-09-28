---
layout: Conceptual
title: Sample queries for hardware inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-hardware-inventory-configuration-manager
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
description: Sample queries that show how to join hardware inventory views to other views that contain system data.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 22d95978-233b-fcdc-11ca-356d4970204b
document_version_independent_id: 4a1b7307-e1e7-813e-0ea2-7f3acc4a3627
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-hardware-inventory-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-hardware-inventory-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-hardware-inventory-configuration-manager.md
cmProducts: []
platformId: 23737119-ee9b-957a-1721-c2e4f7698232
---

# Sample queries for hardware inventory - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join Configuration Manager hardware inventory views to other views that contain system data. Hardware inventory views use the **ResourceID** column when joining to other views.

## List all client OS versions

The following query lists all inventoried Configuration Manager client computers and the operating system and service pack that are running on the client computer. The **v\_GS\_OPERATING\_SYSTEM** hardware inventory view and **v\_R\_System** discovery view are joined by using the **ResourceID** column, and the results are sorted by the computer name.

```sql
SELECT SYS.Name0,
         OS.Caption0,
         OS.CSDVersion0,
         OS.ResourceID
FROM v_GS_OPERATING_SYSTEM OS
INNER JOIN v_R_System SYS
    ON OS.ResourceID = SYS.ResourceID
```

## List clients with hardware inventory scans more than two days old

The following query lists all active Configuration Manager clients that have not been scanned for hardware inventory in more than two days. The **v\_GS\_WORKSTATIONSTATUS** hardware inventory view and **v\_RA\_System\_SMSInstalledSites** discovery view are joined to the **v\_R\_System** discovery view by using the **ResourceID** column.

```sql
    SELECT SYS.Netbios_Name0 as 'Computer Name', 
    SIS.SMS_Installed_Sites0 as 'SMS Site', WS.LastHWScan, 
    DATEDIFF(day,WS.LastHWScan,GETDATE()) as 'Days Since HWScan' 
    FROM v_GS_WORKSTATION_STATUS WS INNER JOIN v_R_System SYS 
    ON WS.ResourceID = SYS.ResourceID INNER JOIN v_RA_System_SMSInstalledSites SIS 
    ON WS.ResourceID = SIS.ResourceID 
    WHERE SYS.Client_Type0 = 1 AND SYS.Active0 = 1 AND 
    WS.LastHWScan < DATEADD([day],-2,GETDATE()) 
```