---
layout: Conceptual
title: Content infrastructure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/manage-content-and-content-infrastructure
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
description: Learn how to deploy and then manage your content management infrastructure for Configuration Manager.
ms.date: 2017-02-07T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: b6b3ebef-75c0-2351-b165-aaf1c60f7660
document_version_independent_id: 4a39a68a-6cda-74e3-c9a5-8eae7a3b7e17
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/manage-content-and-content-infrastructure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/manage-content-and-content-infrastructure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/manage-content-and-content-infrastructure.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 06c3ed2f-285e-abd3-d9eb-d0b18f1d636e
---

# Content infrastructure - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you are ready to set up and then manage your content management infrastructure for Configuration Manager, use the information in the following topics:

- [Install and configure distribution points for Configuration Manager](install-and-configure-distribution-points). Before you can deploy content, you must install and set up distribution points. Then you can set up distribution point groups to help simplify management of content across your infrastructure. The information in this topic can help you complete these tasks, and details the deep and varied settings supported by individual distribution points.
- [Deploy and manage content for Configuration Manager](deploy-and-manage-content). Content deployment transfers files and software to distribution point servers throughout your network. In addition to a simple transfer, you can prestage content, which is a method that can help you avoid excessive use of network bandwidth. The information in this topic can help you with the basic tasks of sending that content or using pre-staged content effectively.
- [Monitor content you have distributed with Configuration Manager](monitor-content-you-have-distributed). As you deploy content, you can monitor its status across your infrastructure. You can also redistribute content that fails to reach distribution points, or cancel distributions that remain in progress. The information in this topic helps you understand how to monitor your content, including how to fix some problems when the transfer of content fails.