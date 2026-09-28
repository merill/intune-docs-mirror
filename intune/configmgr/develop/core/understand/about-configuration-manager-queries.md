---
layout: Conceptual
title: Configuration Manager Queries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-queries
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
description: Create and run the queries that are accessible in the Configuration Manager console under Queries.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 337e3571-f90c-1847-c884-6af300c45ebb
document_version_independent_id: 2beb6884-7eb6-0f7a-9e82-beae00aca5ca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/about-configuration-manager-queries.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/about-configuration-manager-queries
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/about-configuration-manager-queries.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 3ece4f2e-9de1-753a-5d45-829e5995aa4d
---

# Configuration Manager Queries - Configuration Manager | Microsoft Learn

You can create and run the queries that are accessible in the Configuration Manager console under **Queries**.

The queries can be used to locate objects in a Configuration Manager site that match your query criteria. These objects include items such as specific types of computers or user groups. Queries can return most types of Configuration Manager objects, including sites, collections, packages, and saved queries themselves. However, queries are most useful for extracting information that is related to resource discovery, inventory data, and status messages.

Note

For more information, see [Introduction to queries](../../../core/servers/manage/introduction-to-queries).

## SMS\_Query

Configuration Manager queries are defined by `SMS_Query` object instances. The query is a WQL query and is defined in the `Expression` property. For more information about WQL, see [Configuration Manager Extended WMI Query Language](extended-wmi-query-language).

Each query has a unique identifier assigned to it by the SMS Provider and can be used to get a specific query. For information about running a query, see [How to Run a Configuration Manager Query](how-to-run-a-query).

You can also create queries by creating instances of `SMS_Query`. When you create a query, it is displayed in the Configuration Manager console under **Queries**. If you want to, you can limit the results returned to those resources that belong to a specific collection. For more information about creating queries, see [How to Create a Configuration Manager Query](how-to-create-a-configuration-manager-query).