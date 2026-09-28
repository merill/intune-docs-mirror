---
layout: Conceptual
title: Objects Overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview
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
description: The Configuration Manager objects are instances of Configuration Manager-specific WMI classes managed by the SMS Provider.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: fa88a3af-04b7-ef5d-983b-155a18e942b8
document_version_independent_id: 93a24b48-003f-bdb8-9f34-3d222efaa28b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-objects-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-objects-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-objects-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5c549f92-4d34-8c38-dee4-d8749c42ca34
---

# Objects Overview - Configuration Manager | Microsoft Learn

The Configuration Manager objects are instances of Configuration Manager-specific Windows Management Instrumentation (WMI) classes that are managed by the SMS Provider. The Configuration Manager object class categories are described in the following table.

| Configuration Manager Object Class Category | Description |
| --- | --- |
| Software distribution | Objects associated with the software distribution feature of Configuration Manager, such as advertisement, collection, package, and program objects. |
| Scheduling | Organizes scheduled Configuration Manager events, such as inventory updates. |
| Site | Contains information about Configuration Manager sites. |
| Security | Describes the permissions granted to users and user groups to operate on specific Configuration Manager-secured objects, such as program and package objects. |
| Query | Describes Configuration Manager site database queries. |
| Resource | Populated when Configuration Manager discovers potential client computers, users, user groups, and other types of objects within the boundaries of the site. |
| Inventory | Provides the structure for inventory operations on Configuration Manager client systems, users, and user groups. |
| Software metering | Describes the metered Configuration Manager resources, such as program files. |
| Status and summarizer | Indicates the status of Configuration Manager sites, components, and software distribution operations. |
| Collected files | Contains information about files collected from clients. |

## DebugView

To show SMS Provider object property values in the Configuration Manager console results pane, start the console with the following command line:

&lt;InstallationDirectory&gt;\Microsoft.ConfigurationManagement.exe /SMS:DebugView=1

For more information, see [Configuration Manager console command-line options](../../../core/servers/manage/admin-console#command-line-options).