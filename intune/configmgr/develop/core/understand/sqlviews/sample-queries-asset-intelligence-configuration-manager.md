---
layout: Conceptual
title: Sample queries for asset intelligence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-asset-intelligence-configuration-manager
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
description: Sample queries that show how to join the most common Asset Intelligence views to other views.
ms.date: 2020-12-09T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 23fda686-e17b-01ca-1e3e-fdbbe7a5b0ac
document_version_independent_id: 8c0a9e98-1941-629d-9c10-e2586e8b0f9f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-asset-intelligence-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-asset-intelligence-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-asset-intelligence-configuration-manager.md
cmProducts: []
platformId: 8346818a-adcc-6d2c-a0cf-08b988932562
---

# Sample queries for asset intelligence - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join the most common Asset Intelligence views to other views.

## Joining asset intelligence views

The following sample query demonstrates how to join asset intelligence views to asset intelligence hardware inventory and discovery views. Most often, the asset intelligence hardware inventory views will be used when creating asset intelligence reports for resources and joined to other views by using the **ResourceID** column. The asset intelligence views can be joined to the asset intelligence hardware inventory views to list product information by using the **SoftwareCode** column.

This sample query lists the publisher, product, installation date, and installation path for software identified during a hardware inventory on the Workstation1 computer. The query results are sorted by the latest installation date and then product name. The query joins the **v\_GS\_INSTALLED\_SOFTWARE** asset intelligence hardware inventory view to the **v\_LU\_SoftwareCode** asset intelligence view by using the **SoftwareCode0** and **SoftwareCode** columns, respectively, and then joins the asset intelligence views, **v\_LU\_SoftwareList** and **v\_LU\_SoftwareCode** by using the **SoftwareID** columns. Finally, the query joins the **v\_GS\_INSTALLED\_SOFTWARE** view with the **v\_R\_System** discovery view by using the **ResourceID** column. A LEFT OUTER JOIN is used when joining the views to display only information contained in the **v\_GS\_INSTALLED\_SOFTWARE** view.

```sql
    SELECT v_LU_SoftwareList.CommonPublisher AS Publisher, 
      v_LU_SoftwareList.CommonName AS [Product Name], 
      v_LU_SoftwareList.CommonVersion AS Version, 
      v_GS_INSTALLED_SOFTWARE.InstallDate0 AS [Install Date], 
      v_GS_INSTALLED_SOFTWARE.InstalledLocation0 AS Path 
    FROM v_GS_INSTALLED_SOFTWARE LEFT OUTER JOIN v_LU_SoftwareCode ON 
      v_GS_INSTALLED_SOFTWARE.SoftwareCode0 = v_LU_SoftwareCode.SoftwareCode INNER JOIN v_LU_SoftwareList ON  v_LU_SoftwareList.SoftwareID = v_LU_SoftwareCode.SoftwareID LEFT OUTER JOIN v_R_System ON  v_GS_INSTALLED_SOFTWARE.ResourceID = v_R_System.ResourceIDWHERE (v_R_System.Netbios_Name0 LIKE 'Workstation1') 
    ORDER BY [Install Date] DESC, [Product Name] 
```