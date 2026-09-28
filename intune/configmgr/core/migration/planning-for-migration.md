---
layout: Conceptual
title: Plan for migration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-for-migration
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
description: Learn about sites and hierarchies before you migrate data to a Configuration Manager current branch destination hierarchy.
ms.date: 2017-01-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: edac297e-7a49-83dd-84b4-ae3c2cc344f0
document_version_independent_id: 5f19adc5-c90e-ce24-0d91-27de56d574aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/migration/planning-for-migration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/migration/planning-for-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/migration/planning-for-migration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: ff2479b3-74a0-7890-0db2-3ca924e2caf4
---

# Plan for migration - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you migrate data to a Configuration Manager current branch destination hierarchy, make sure that you are familiar with sites and hierarchies in Configuration Manager. For more about sites and hierarchies, see [Fundamentals of Configuration Manager](../understand/fundamentals).

Install a Configuration Manager current branch hierarchy to be the destination hierarchy before you migrate data from a supported source hierarchy.

After you install the destination hierarchy, set up the management features and functions that you want to use in your destination hierarchy before you start to migrate data.

Additionally, you might have to plan for overlap between the source hierarchy and your destination hierarchy. For example, you might set up the source hierarchy to use the same network locations or boundaries as your destination hierarchy, and you then install new clients to your destination hierarchy and use automatic site assignment. In this scenario, because a newly installed Configuration Manager client can select a site to join from either hierarchy, the client might incorrectly assign to your source hierarchy. Therefore, plan to assign each new client in the destination hierarchy to a specific site in that hierarchy instead of using automatic site assignment.

For more about site assignments, see [Client site assignment considerations](../plan-design/hierarchy/interoperability-between-different-versions#client-site-assignment-considerations) in [Interoperability between different versions of Configuration Manager](../plan-design/hierarchy/interoperability-between-different-versions).

Use the following articles to help you plan how to migrate a supported source hierarchy to a Configuration Manager destination hierarchy:

- [Prerequisites for migration](prerequisites-for-migration)
- [Administrator checklists for migration planning](administrator-checklists-for-migration-planning)
- [Determine whether to migrate data to Configuration Manager current branch](determine-whether-to-migrate-data)
- [Plan a source hierarchy strategy](planning-a-source-hierarchy-strategy)
- [Administrator checklists for migration planning](administrator-checklists-for-migration-planning)
- [Plan a client migration strategy](planning-a-client-migration-strategy)
- [Plan a content deployment migration strategy](planning-a-content-deployment-migration-strategy)
- [Plan for the migration of Configuration Manager objects to Configuration Manager current branch](planning-for-the-migration-of-objects)
- [Plan to monitor migration activity](planning-to-monitor-migration-activity)
- [Plan to complete migration](planning-to-complete-migration)