---
layout: Conceptual
title: Software Distribution Overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview
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
description: Learn how the Configuration Manager expands the abilities of system administrators to centrally manage computers effectively by providing a refined tool set for software distribution.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 8e012655-3551-ab90-686d-69acbc8521de
document_version_independent_id: 5521bb9f-58f9-9ed2-e83c-0d8fa86ea651
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/software-distribution-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/software-distribution-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/software-distribution-overview.md
cmProducts: []
platformId: c19a95b7-c45d-21db-3496-0c1476a7ef90
---

# Software Distribution Overview - Configuration Manager | Microsoft Learn

With this release, Configuration Manager expands the abilities of system administrators to centrally manage computers effectively. Building on the capabilities provided by Configuration Manager 2007, Configuration Manager provides a refined tool set for software distribution.

## Distributing Software

The software distribution process advertises packages, which contain programs, to members of a collection. The client then installs the software from specified distribution points. The order in which you create the components that make up the software distribution process is important.

1. Create an instance of `SMS_Package`.
2. Create an instance of `SMS_Program`.
3. If an existing collection does not identify the users to whom you want to distribute the software, create a new collection by creating an instance of `SMS_Collection`.
4. If the package contains source files, define a distribution point for the package by creating an instance of `SMS_DistributionPoint`.
5. Create an instance of `SMS_Advertisement`.

    The following topics show how to create the software distribution components:

    [How to Create a Package](how-to-create-a-package)

    [How to Create a Program](how-to-create-a-program)

    [How to Assign a Package to a Distribution Point](how-to-assign-a-package-to-a-distribution-point)

    [How to Create an Advertisement](how-to-create-an-advertisement)