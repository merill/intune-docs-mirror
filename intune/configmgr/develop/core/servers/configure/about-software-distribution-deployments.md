---
layout: Conceptual
title: Software Distribution Deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-software-distribution-deployments
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
description: In Configuration Manager, after a software distribution package has been created, with programs to tell client computers what to do with the package, you need to advertise the program.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 7fdd1322-30d8-fe74-f1a8-8b63eb2d59b7
document_version_independent_id: 68b1af5c-2b23-dd3d-7cc7-31e8b749d46f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/about-software-distribution-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/about-software-distribution-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/about-software-distribution-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0dadf499-f7d4-da88-258d-13cc13eccf09
---

# Software Distribution Deployments - Configuration Manager | Microsoft Learn

In Configuration Manager, after a software distribution package has been created, with programs to tell client computers what to do with the package, you need to advertise the program that you want the clients to run. Advertising the program makes a program available to a specified collection of clients.

Advertisements are evaluated by Configuration Manager to determine which clients receive a specific program to run on their computers. An advertisement specifies the following information:

- The specific program to run on the client.
- The target collection of computers, users, or user groups that are to receive the program.
- The schedule that specifies when the program is available to clients. If there are assigned (mandatory) advertisements, other options such as Wake On LAN and ignoring maintenance windows can be used with this schedule.

    The site's clients can't receive advertised programs until you enable the software distribution advertised programs client agent on the site's clients. The **Advertised Programs Client Agent** performs the necessary software distribution-related tasks on these clients, primarily allowing the clients to receive and run the programs that you advertise.