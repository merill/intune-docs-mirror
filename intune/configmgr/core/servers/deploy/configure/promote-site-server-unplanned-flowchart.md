---
layout: Conceptual
title: Flowchart - unplanned promotion - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/promote-site-server-unplanned-flowchart
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
description: A flowchart diagram for how the Configuration Manager site server in passive mode is promoted to active when the current site server in active mode is offline.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ae238dea-6a35-fd11-d532-e26ad6cb9c31
document_version_independent_id: de674229-cf74-d450-c584-45796ca239e5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/promote-site-server-unplanned-flowchart.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/promote-site-server-unplanned-flowchart
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/promote-site-server-unplanned-flowchart.md
cmProducts: []
platformId: 0efe7a4f-45ec-8e7c-f071-664453e72aa5
---

# Flowchart - unplanned promotion - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This flowchart diagram shows the process by which a site server in passive mode is promoted to the site server in active mode when the current site server in active mode is offline. In this example, the current site server in active mode isn't fully operational, for example it is disconnected from the network or powered off. For more information, see the following articles:

- [Site server high availability](site-server-high-availability)
- [Flowchart - Promote site server (planned)](promote-site-server-flowchart)
- [Flowchart - Set up a site server in passive mode](passive-site-server-flowchart)

![Flowchart diagram to promote a site server in passive mode, unplanned process](media/promote-site-server-unplanned-flowchart.png)