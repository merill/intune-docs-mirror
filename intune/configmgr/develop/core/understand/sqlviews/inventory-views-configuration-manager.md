---
layout: Conceptual
title: Inventory views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/inventory-views-configuration-manager
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
description: Hardware and software inventory information about the clients, files, and products, in the Configuration Manager hierarchy.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3dc8de18-6947-60ae-6541-3136eae11aee
document_version_independent_id: acb830df-98d1-b7d9-ee92-ee7e8b33f8cf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/inventory-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/inventory-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/inventory-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 7ba80433-a1d2-21a3-e866-4a66fdb1d9f7
---

# Inventory views - Configuration Manager | Microsoft Learn

Inventory views contain hardware and software inventory information about the clients, files, products, and so forth, in the Configuration Manager hierarchy. Configuration Manager collects inventory data when you enable the Hardware Inventory Client Agent or Software Inventory Client Agent. Because you can configure which hardware inventory to collect during the hardware inventory scan cycle and which file types to scan for during the software inventory scan cycle, each site will have a unique set of inventory that is collected.

For each Configuration Manager site, it's possible to retrieve a list of the hardware and software inventory schema to determine exactly what is inventoried. The articles in this section provide examples of how to do get the hardware and software inventory lists, and detailed information about the typical Configuration Manager SQL views.