---
layout: Conceptual
title: Sample queries for software metering - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-metering-configuration-manager
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
description: Sample queries that show how to join the most common software metering views to other views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a53daa91-9061-2b16-df12-25ff33a9667e
document_version_independent_id: 4fd9bf82-124f-fd39-9b62-e863d3551ee6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-metering-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-software-metering-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-metering-configuration-manager.md
cmProducts: []
platformId: 8220a1ba-8c7d-7965-0372-4286655f5e50
---

# Sample queries for software metering - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join the most common software metering views to other views.

## Joining software metering, software inventory, and discovery views

The following query lists all resources that have run metered files, including the resource name, file ID, file name, file version, and start time. The **v\_MeterData** software metering view is joined to the **v\_ProductFileInfo** software inventory view by using the **FileID** column and to the **v\_R\_System** discovery view by using the **ResourceID** column.

```sql
    SELECT SYS.Netbios_Name0, PFI.FileID, PFI.FileName, 
    PFI.FileVersion, MD.StartTime 
    FROM v_MeterData MD INNER JOIN v_ProductFileInfo PFI 
    ON MD.FileID = PFI.FileID INNER JOIN v_R_System SYS 
    ON MD.ResourceID = SYS.ResourceID 
    ORDER BY SYS.Netbios_Name0, PFI.FileName 
```

## Joining software metering, status, and software inventory views

The following query lists all users who have run metered files. The query returns the user domain, user name, file name, file version, usage count, total time of usage, and the last time the file was used. The **v\_MeteredUser** software metering view is joined to the **v\_MonthlyUsageSummary** status view by using the **MeteredUserID** column. The **v\_MonthlyUsageSummary** status view is joined to the **v\_GS\_SoftwareFile** software inventory view by using the **FileID** column.

```sql
    SELECT MU.Domain, MU.UserName, SF.FileName, SF.FileVersion, 
    MUS.UsageCount, MUS.UsageTime, MUS.LastUsage 
    FROM v_MeteredUser MU INNER JOIN v_MonthlyUsageSummary MUS 
    ON MU.MeteredUserID = MUS.MeteredUserID INNER JOIN 
    v_GS_SoftwareFile SF ON MUS.FileID = SF.FileID 
    ORDER BY MU.Domain, MU.UserName, SF.FileName 
```