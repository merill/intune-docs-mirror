---
layout: Conceptual
title: Software inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/introduction-to-software-inventory
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
description: Get an introduction to software inventory in Configuration Manager.
ms.date: 2019-04-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: e06f4bc2-6add-a61c-d9f3-be04cdb8b411
document_version_independent_id: f9c9b8e0-4e5f-dacd-4ad3-b9050a7f85bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/introduction-to-software-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/introduction-to-software-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/introduction-to-software-inventory.md
cmProducts: []
platformId: 2f0b260e-84a1-1e8e-f52b-e5666f51371a
---

# Software inventory - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use software inventory to collect information about files on client devices. Software inventory can also collect files from client devices and store them on the site server. Software inventory is collected when you select the **Enable software inventory on clients** setting in client settings. You can also schedule the operation in client settings.

After you enable software inventory and the clients run a software inventory cycle, the client sends the information to a management point in the client's site. The management point then forwards the inventory information to the Configuration Manager site server, which stores the information in the site database.

There are a few ways to view software inventory data:

- [Create queries](../../../servers/manage/create-queries) that return devices with specified files.
- Create [query-based collections](../collections/introduction-to-collections) that include devices with specified files.
- [Run reports](../../../servers/manage/introduction-to-reporting) that provide details about files on devices.
- Use [Resource Explorer](use-resource-explorer-to-view-software-inventory) to examine detailed information about the files that were inventoried and collected from client devices.

When software inventory runs on a client device, the first report is a full inventory. Subsequent reports contain only delta inventory information. The site server processes delta information in the order received. If delta information for a client is missing, the site server rejects further delta information and directs the client to run a full inventory.

Configuration Manager can discover dual-boot computers but only returns inventory information from the operating system that's active at the time of inventory.