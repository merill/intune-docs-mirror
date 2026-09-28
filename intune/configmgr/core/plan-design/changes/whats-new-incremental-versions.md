---
layout: Conceptual
title: Incremental versions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-incremental-versions
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
description: Learn about what's new in the latest update for Configuration Manager.
ms.date: 2025-03-31T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 9e242a7b-aaf8-fb60-3661-d7339b0d0a4f
document_version_independent_id: 354ad749-0275-24a9-ac85-111435f2f4c2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-incremental-versions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-incremental-versions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-incremental-versions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 2f2732cb-9c64-b132-54a2-b4b89d506b49
---

# Incremental versions - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager uses an in-console [updates and servicing](../../servers/manage/updates) process. This update process makes it easy to discover and install Configuration Manager updates. There are no more service packs or cumulative update versions to track and install. You don't have to search for the download of the most recent release or updates.

To update the product to a new version of the current branch, use the Configuration Manager console install then. A few times each year, Microsoft releases new versions that include product updates. Each version also introduces new features. When you install an update with new features, you can choose to use those features. For more information, see [Prepare to install in-console updates for Configuration Manager](../../servers/manage/prepare-in-console-updates).

Different update versions are identified by year and month. For example, version 1511 identifies November 2015 (the month when Configuration Manager current branch was first released to manufacturing). Later updates have version names like 2107, which indicates an update that was created in July 2021. These update versions are key to understanding the incremental version of your Configuration Manager installation, and what features are available to enable in your environment.

## Supported versions

Refer to the *Supported versions* section of the [Updates and Servicing](../../servers/manage/updates) page for the latest version information.

Each update version remains in support for 18 months from its initial availability date. Stay current with the most recent update version. For more information, see [Support for Configuration Manager current branch versions](../../servers/manage/current-branch-versions-supported).