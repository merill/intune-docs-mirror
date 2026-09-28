---
layout: Conceptual
title: Synchronize the Software Update Point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-synchronizing-the-software-update-point
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
description: In Configuration Manager, software updates must be synchronized before the update information is available in the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: de712ca4-49f3-d515-33f8-2ead764fa4a9
document_version_independent_id: d28e840f-c96b-f766-b42a-bf8d38fc4777
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/about-synchronizing-the-software-update-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/about-synchronizing-the-software-update-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/about-synchronizing-the-software-update-point.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 26fbe91a-cb66-02d7-2216-328c63cef32d
---

# Synchronize the Software Update Point - Configuration Manager | Microsoft Learn

In Configuration Manager, software updates must be synchronized before the update information is available in the Configuration Manager console. Synchronization is initiated at the highest level site in the hierarchy that has a software update point.

For more information about software updates, see [Deploy and manage software updates](../../sum/understand/software-updates-introduction).

## Software Updates Synchronization

Software updates synchronization in Configuration Manager is the process of retrieving the software updates metadata that meet the configured criteria from the upstream Windows Server Update Services (WSUS) server or from Microsoft Update. The highest site in the Configuration Manager hierarchy with a software update point (most likely the central site) synchronizes with Microsoft Update. This synchronization can be scheduled as part of the software update point properties, or it can be manually initiated.

There are two types of synchronization:

- A full synchronization, which synchronizes the whole catalog of updates on the WSUS server. At the end of the full synchronization, the Configuration Manager database will match the content of WSUS filtered by the current subscription.
- A delta synchronization, which synchronizes only changes (adds and removals) that occurred since the last successful synchronization. A delta synchronization won't examine any updates synchronized earlier and not changed since.

Important

While they are nearly identical functionally, a full synchronization will potentially repair updates from previous synchronizations that have gotten damaged or deleted. A delta synchronization will not repair any updates from previous synchronizations.

in Configuration ManagerSP1 most synchronizations, both manual and scheduled, perform a delta synchronization. A synchronization will escalate to a full synchronization if there are configuration changes that require a full synchronization, such as: switching to a different default SUP, changes in the subscription, changes in the supersedence mode or window. A synchronization will also escalate to a full synchronization periodically every 7 days (a period configurable in the site control file under "Full Sync Interval (days)").