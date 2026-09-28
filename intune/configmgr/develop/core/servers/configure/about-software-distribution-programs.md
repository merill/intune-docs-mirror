---
layout: Conceptual
title: Software Distribution Programs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-software-distribution-programs
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
description: Learn all about software distribution programs and how they are packaged and made available to a collection of clients.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: d5e2d20c-2f7e-60d1-0623-560e07879c56
document_version_independent_id: d39d35a7-b60a-f25a-86b8-32c29d68696a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/about-software-distribution-programs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/about-software-distribution-programs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/about-software-distribution-programs.md
cmProducts: []
platformId: 05f8e324-131f-8377-b364-5733f168e18a
---

# Software Distribution Programs - Configuration Manager | Microsoft Learn

Programs are commands that are associated with a Configuration Manager package that tell a client what should occur on the client computer when the package is received. You can associate almost any activity with a program. For example, a program can be used to install new software on clients, distribute data files, run virus-detection software, or update client configuration.

Every deployable package must contain at least one program, but you can specify more than one, if needed. A package can often have several programs associated with it, allowing the package to be run in different ways on different clients. This is often the case when you are installing a new application on a client computer and want to create programs to perform either a typical, minimum, or custom installation.

Although the package contains the application, files, or information that need to be applied to the client computers, the program is responsible for defining how that application is to be used. As a result, the program must include all appropriate references to script files or command switches. The program also defines the platform and environment in which the package can run, which means that you might have a program for each suitable platform when you have clients using different operating systems.

After you create a program for a given package, you can make that program and package available to a collection of clients by using an advertisement.