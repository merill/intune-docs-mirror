---
layout: Conceptual
title: How to modify reports - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-modify-configuration-manager-reports
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
description: Information about viewing the properties of, and modifying Configuration Manager reports.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 5818e56e-62a3-bf60-925c-f1fc68796034
document_version_independent_id: 05de48ef-7865-d637-2af9-2afde4c96431
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/how-to-modify-configuration-manager-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/how-to-modify-configuration-manager-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/how-to-modify-configuration-manager-reports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: ce49b3b9-2ae9-2391-6eac-baebf38660f8
---

# How to modify reports - Configuration Manager | Microsoft Learn

The procedures in this topic help you to view the properties of, and modify Configuration Manager reports.

## How to view the general properties of a report

You can view general properties for a report in the Configuration Manager console. Use the following procedure to view the properties of a report.

### To view the general properties of a report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. From the list of reports, select the report that you want to view properties for and then, in the **Home** tab, in the **Properties** group, select **Properties**.
4. In the *report name*�**Properties** dialog box, you can view general information about the report, create and view report subscriptions and view security information about the report.
5. Close the *report name*�**Properties** dialog box.

## How to modify a report

Use SQL Server Report Builder to modify reports. Report Builder can be opened directly from the Configuration Manager console. Use the following procedure to modify a Configuration Manager report.

### To modify a report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. From the list of reports, select the report that you want to view properties for and then, in the **Home** tab, in the **Report Group** group, select **Edit**.
4. In SQL Server Report builder, make the necessary modifications to the report.
5. Save your report, and then close Report Builder.