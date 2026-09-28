---
layout: Conceptual
title: Custom database file locations - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/custom-locations-for-site-database-files
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
description: Learn how to specify custom locations for SQL Server database files.
ms.date: 2020-10-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 8840f7e8-a2fd-0dbf-33d8-41629c873d3b
document_version_independent_id: 2f648ff5-85d5-8c0e-771d-d89d2231d16e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/custom-locations-for-site-database-files.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/custom-locations-for-site-database-files
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/custom-locations-for-site-database-files.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: ef582b6f-35bf-67d0-74e8-511668b33a55
---

# Custom database file locations - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager supports custom locations for SQL Server database files.

Note

The option to specify non-default file locations isn't available when you use a SQL Server Always On failover cluster instance.

During setup of a new primary site or central administration site, you can:

- **Specify non-default file locations for the site database**: Configuration Manager setup then creates the site database using these locations.
- **Specify the use of a pre-created SQL Server database that uses custom file locations**: Configuration Manager setup then uses that pre-created database and its pre-configured file locations.

After setup, you can change the location of the site database files. This requires you to stop the site and edit the file location in SQL Server:

1. On the Configuration Manager site server, stop the **SMS\_Executive** service.
2. Move the database in SQL Server. For more information, see [Move User Databases](/en-us/sql/relational-databases/databases/move-user-databases).
3. After you complete the database file move, restart the **SMS\_Executive** service on the Configuration Manager site server.