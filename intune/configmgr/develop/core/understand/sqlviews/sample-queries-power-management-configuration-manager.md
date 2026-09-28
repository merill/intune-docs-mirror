---
layout: Conceptual
title: Sample queries for power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-power-management-configuration-manager
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
description: Sample queries that show how to join power management views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 28db73d7-fb1d-4f08-7f30-74e0b205f8dd
document_version_independent_id: 452b4063-7725-64e7-0a83-4a64ada07c60
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-power-management-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-power-management-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-power-management-configuration-manager.md
cmProducts: []
platformId: 4c46fd16-7fc5-1c46-2aa0-3a29876bb20b
---

# Sample queries for power management - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join power management views to other views.

## Joining power management views to discovery views

The following query lists all computers, by Netbios name, that are excluded from power management because the user chose to exclude them.

The query returns the Netbios name and the domain of the computer and also the client opt-out setting where this value is 1 (indicating that the computer has been excluded from power management).

```sql
    SELECT        v_R_System.Name0, v_R_System.Resource_Domain_OR_Workgr0, 
                             v_GS_POWER_MANAGEMENT_CLIENTOPTOUT_SETTINGS.IsClientOptOut0
    FROM            v_R_System INNER JOIN
                             v_GS_POWER_MANAGEMENT_CLIENTOPTOUT_SETTINGS ON 
                             v_R_System.ResourceID = v_GS_POWER_MANAGEMENT_CLIENTOPTOUT_SETTINGS.ResourceID
    WHERE        (v_GS_POWER_MANAGEMENT_CLIENTOPTOUT_SETTINGS.IsClientOptOut0 = 1)
```