---
layout: Conceptual
title: About upgrade, update, and install - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/upgrade-update-install
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
description: Learn the difference between the terms Install, Update, and Upgrade, when managing Configuration Manager infrastructure.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: d695f17c-8460-59aa-b280-8961106b1104
document_version_independent_id: b3907348-6b58-a690-38f7-78d694465292
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/upgrade-update-install.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/upgrade-update-install
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/upgrade-update-install.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 25bf1a62-2a80-3c22-b8ed-bcfd0063a778
---

# About upgrade, update, and install - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When managing Configuration Manager sites and hierarchy infrastructure, the terms *upgrade*, *update*, and *install* are used to describe three separate concepts.

## Upgrade

*Upgrade* or *in-place upgrade*, is used when converting your Configuration Manager 2012 site or hierarchy to one that runs Configuration Manager current branch.

When you upgrade System Center 2012 Configuration Manager to Configuration Manager current branch, you continue to use the same servers to host your sites and site servers, and you retain your existing data and configurations for Configuration Manager. This is different from [Migration](../migration/migrate-data-between-hierarchies) which is a way to retain your configurations and data about managed devices while using new Configuration Manager current branch sites installed to new hardware.

For more information, see [Upgrade to Configuration Manager](../servers/deploy/install/upgrade-to-configuration-manager).

## Update

*Update* is used for installing in-console updates for Configuration Manager, and for out-of-band updates which are updates that can't be delivered from within the Configuration Manager console. In-console updates can modify the version of your Current Branch site (or Technical Preview site) so that it runs a higher version. For example, if your site runs version 1806, you can install an update for version 1810. Updates can also install fixes for a known issue, without modifying the site version.

Typically, updates add security fixes, quality improvements, and new features to your existing deployment. If you use the Technical Preview branch, an update can install a newer version of the Technical Preview.

- You choose when to install the in-console update, starting at the top-tier site of your hierarchy.
- You can install any update that is available from within the console. For example, if your site runs version 1802 and both 1806 and 1810 are offered, you should consider installing version 1810 because each version includes the features that were first made available in previously released versions.
- After a new update completes installation at your top-tier site, child primary sites automatically start the process to update. However, you can set [Service Windows](../servers/manage/service-windows) to control the timing of updates.
- Secondary sites don't automatically install updates. Instead, you manually start the update from within the Configuration Manager console.

For more, see [Updates for Configuration Manager](../servers/manage/updates), and [Technical Preview for Configuration Manager](../get-started/technical-preview).

## Install

*Install* is used when creating a new Configuration Manager hierarchy from scratch, or adding more sites to an existing hierarchy.

When you install a new primary site or central administration site, the location of setup.exe and its related source files that you use depend on your installation scenario.

For more, see [Prepare to install sites](../servers/deploy/install/prepare-to-install-sites).