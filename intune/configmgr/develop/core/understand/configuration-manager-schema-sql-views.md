---
layout: Conceptual
title: Schema SQL Views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-sql-views
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
description: Creates schema information views. These are particularly useful for determining the names for custom inventory resource type (architecture) tables.
ms.date: 2018-03-08T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6aebc7ca-a2e0-7e02-a00d-166fd6acbcd0
document_version_independent_id: 89792129-8db7-f0ea-7130-d32e27a04cc6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-schema-sql-views.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-schema-sql-views
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-schema-sql-views.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: b7c37e00-7094-1d36-e84a-3ec3d6a98dd5
---

# Schema SQL Views - Configuration Manager | Microsoft Learn

In Configuration Manager, a number of schema information views are created to get information about the names of all the available views and the schema for the inventory and discovery classes. These are particularly useful for determining the names for custom inventory resource type (architecture) tables. The following table shows a list of these schema information views.

| View | Description | Sample Query |
| --- | --- | --- |
| v\_SchemaViews | Lists all the views in the view schema family. | `Select ViewName, Type from v_SchemaViews order by ViewName` |
| v\_ResourceMap | Lists the resource type views. | `select * from v_ResourceMap` |
| v\_ResourceAttributeMap | Lists attributes for each resource type. | `select * from v_ResourceAttributeMap` |
| v\_GroupMap | Lists inventory groups for each inventory architecture. | `select * from v_GroupMap` |
| v\_GroupAttributeMap | Lists attributes for each inventory group. | `select * from v_GroupAttributeMap` |
| v\_ReportViewSchema | Parallel to the `SMS_ReportViewSchema` class, this view lists all the classes and properties. | `select * from v_ReportViewSchema` |

For more information about how the SQL views map to their WMI class equivalents, see [Configuration Manager Schema View Mapping](configuration-manager-schema-view-mapping)