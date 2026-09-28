---
layout: Conceptual
title: How to view the SQL Statement for reports - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-view-sql-statement-configuration-manager-reports
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
description: Information to find out what SQL statement is used in a Configuration Manager report.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4fcaad7b-ec5f-aa29-5a58-d69744a0319b
document_version_independent_id: 959c2d50-07c8-788b-2c82-3f42a015275c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/how-to-view-sql-statement-configuration-manager-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/how-to-view-sql-statement-configuration-manager-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/how-to-view-sql-statement-configuration-manager-reports.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 534d24c2-0f6c-4da8-a4e6-138a8f0170ab
---

# How to view the SQL Statement for reports - Configuration Manager | Microsoft Learn

Reports in Configuration Manager can be based on simple SQL statements or very complex ones that prompt the user for information, join several Microsoft SQL Server views, and use filters to limit the results. Use the following procedure to find out what SQL statement is used in a Configuration Manager report.

## To view the SQL statement for a report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. Select the report for which you want to view the SQL statement and then, in the **Home** tab, in the **Report Group** group, select **Edit**.
4. The Report Builder window opens. In the **Report Data** pane, expand **Datasets** to view the data sets for the report.
5. Double-click a dataset to open the **Dataset Properties** dialog box.

    The first dataset is typically (but not always), the main SQL statement for the report. Other datasets might contain the SQL statements that can be used to present a list of items for a user to choose from, such as a list of computers.
6. You can view and modify the SQL statement for the dataset in the **Query** field.
7. Close the **Dataset Properties** dialog box.
8. Close Report Builder.