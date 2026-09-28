---
layout: Conceptual
title: Introduction to queries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-queries
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
description: Create and run queries to locate objects in a Configuration Manager hierarchy that match your query criteria.
ms.date: 2019-05-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: a5d8bf2d-c452-a136-8107-6150a4f0044e
document_version_independent_id: 20b1c0b0-3229-1218-11a1-ff2b4de874fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/introduction-to-queries.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/introduction-to-queries
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/introduction-to-queries.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 50a2de6a-44d6-a5c5-496a-d8779ee36562
---

# Introduction to queries - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can create and run queries to locate objects in a Configuration Manager hierarchy that match your query criteria. These objects include items like specific types of computers or user groups. Queries can return most types of Configuration Manager objects, which include sites, collections, applications, and inventory data.

## Query creation overview

When you create a query, you must specify a minimum of two parameters: where you want to search and what you want to search for. For example, to find the amount of hard drive space that's available on all computers in a Configuration Manager site, you can create a query to search the **Logical Disk** attribute class and the **Free Space (MB)** attribute for available hard drive space.

After you create an initial query, you can specify additional query criteria. For example, you can specify that the query results include only computers that are assigned to a specified site. You can also change how results are displayed so you can view the results in an order that's meaningful to you. For example, you can specify that the results are sorted by the amount of free hard drive space, in either ascending or descending order.

When you create a query, it's stored by Configuration Manager and displayed in the **Queries** node in the **Monitoring** workspace. From this location, you can create new queries and run, update, and manage existing queries.

You can also import a query into a query rule in a Configuration Manager collection. For more information, see [How to create collections](../../clients/manage/collections/create-collections).