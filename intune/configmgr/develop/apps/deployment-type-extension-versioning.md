---
layout: Conceptual
title: Deployment Type Extension Versioning - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/deployment-type-extension-versioning
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
description: Configuration Manager supports in-place versioning for minor upgrades and out-of-place versioning for major upgrades.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 10e9d509-c8d2-86b3-119a-0b7a841fb5e0
document_version_independent_id: 36d3da5d-9704-5b77-0859-3bc7d8005aab
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/deployment-type-extension-versioning.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/deployment-type-extension-versioning
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/deployment-type-extension-versioning.md
cmProducts: []
platformId: 026f776a-76b3-49a9-025c-6568d7210545
---

# Deployment Type Extension Versioning - Configuration Manager | Microsoft Learn

Configuration Manager supports in-place versioning for minor upgrades and out-of-place versioning for major upgrades.

## Versioning

### Minor Revisions

Configuration Manager supports in-place versioning for minor upgrades that are backwards compatible. For in-place versioning, increment the version number.

### Major Revisions

Configuration Manager supports out-of-place versioning for major upgrades that aren't backwards compatible. For out-of-place versioning, it's necessary to create a new extension and technology ID.