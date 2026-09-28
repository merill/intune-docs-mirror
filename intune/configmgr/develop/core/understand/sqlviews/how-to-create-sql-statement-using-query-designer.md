---
layout: Conceptual
title: How to create a SQL statement by using query designer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-create-sql-statement-using-query-designer
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
description: How to create Configuration Manager report queries using Query Designer.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ea2b1477-f5aa-8aea-ffd6-ac334b7345f8
document_version_independent_id: 8574ccc2-c9ff-1d45-0e71-06556844e84e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/how-to-create-sql-statement-using-query-designer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/how-to-create-sql-statement-using-query-designer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/how-to-create-sql-statement-using-query-designer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: e47f8b5a-668c-c059-3985-ed9fc89318f9
---

# How to create a SQL statement by using query designer - Configuration Manager | Microsoft Learn

Query Designer in SQL Server can help you to more easily write SQL queries that can be used in your Configuration Manager reports. Use the following procedures to create Configuration Manager report queries using Query Designer.

## To create a new SQL query in query designer

1. Start Microsoft SQL Server Management Studio.
2. Navigate to *&lt;Computer Name&gt;�*\ Databases \*�&lt;Configuration Manager database name&gt;�*\ Views\*\*.
3. Right-click **Views** and then select **New View**.
4. In the **Add Table** dialog box, select the **Views** tab and then select the views that you want to include in the SQL query.

    Note

    You can select multiple views by holding down the CTRL key.
5. In the design view of query designer, select the columns you want to appear in the report. If you are querying multiple views, you can join these by selecting a column in one view and dragging this over to the same column in another view.
6. Select **Execute SQL** to test the query and see the results.
7. When you are happy with the results returned by the query, copy and paste it from query designer to be used to create your report in Report Builder.