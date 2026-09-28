---
layout: Conceptual
title: See a View by Using SQL Server - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-see-a-configuration-manager-view-by-using-sql-server
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
description: The following examples demonstrate various Microsoft Configuration Manager SQL view queries.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 36f8ba4d-db9a-d880-89cd-cb626990242b
document_version_independent_id: 02a99fb8-a3bd-cb5a-6ff5-3507c3e41f25
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-see-a-configuration-manager-view-by-using-sql-server.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-see-a-configuration-manager-view-by-using-sql-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-see-a-configuration-manager-view-by-using-sql-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 1dc6bf44-f687-d18b-041a-cc3f473b4f17
---

# See a View by Using SQL Server - Configuration Manager | Microsoft Learn

The following examples demonstrate various Microsoft Configuration Manager SQL view queries.

## Examples

#### To determine the display name of a resource type from the resource type number

- In SQL Server, query the Configuration Manager database with the following SQL statement:

```
select DisplayName from v_ResourceMap where ResourceType=5
```

#### To determine discovery properties for a particular resource type

- In SQL Server, query the Configuration Manager database with the following SQL statement:

```
select * from v_ResourceAttributeMap where ResourceType=5
```

#### To list the inventory groups for a particular resource type

- In SQL Server, query the Configuration Manager database with the following SQL statement:

```
select InvClassName from v_GroupMap where ResourceType = 5
```