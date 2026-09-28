---
layout: Conceptual
title: Computer Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-computer-management
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
description: Computer management in Configuration Manager operating system deployment covers the following areas.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: e8fc0101-4d5e-173f-f250-d607cdbffa76
document_version_independent_id: 596271f5-102f-47ce-2b83-8adaddeab938
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-computer-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-computer-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-computer-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bbcb326a-48c4-330f-cb4c-b3bb755920b0
---

# Computer Management - Configuration Manager | Microsoft Learn

Computer management in Configuration Manager operating system deployment covers the following areas.

## Computer Import

To deploy an operating system to a new computer without stand-alone media that is not currently managed by Configuration Manager, the new computer must be added to the Configuration Manager database prior to initiating the operating system deployment process. Although Configuration Manager can automatically discover computers on your network that have a Windows operating system installed, if the computer has no operating system installed you must import the new computer information. For more information, see [How to Import a New Computer into Configuration Manager](how-to-import-a-new-computer-into-configuration-manager).

## Computer Association

A computer association creates a relationship between a source and destination computer for the side-by-side migration of user state data. The source computer is an existing computer that is managed by Configuration Manager, and contains the user state data and settings that will be migrated to a specified destination computer. For more information, see [How to Create an Association Between Two Computers in Configuration Manager](how-to-create-an-association-between-two-computers-in-configuration-manager).

## Computer and Machine Variables

Task sequences can be configured to run simultaneously on multiple computers or on collections. You can specify unique per-computer or per-collection information, such as specifying a unique operating system product key or joining all the members of a collection to a domain. These settings can be configured when you create a task sequence or edit an existing task sequence.

You can assign task sequence variables to a single computer or to a collection. When the task sequence starts to run on the target computer or the collection, the values that are specified are applied to the target computer or collection.

For more information, see the following:

| Task | How to |
| --- | --- |
| Collection variables | [How to Create a Collection Variable in Configuration Manager](how-to-create-a-collection-variable) |
| Computer variables | [How to Create a Computer Variable in Configuration Manager](how-to-create-a-computer-variable) |
| Setting task sequence variables | [How to Set an Operating System Deployment Task Sequence Variable](how-to-set-an-operating-system-deployment-task-sequence-variable) |
| Changing variables in a running task sequence | [How to Use Task Sequence Variables in a Running Configuration Manager Task Sequence](how-to-use-task-sequence-variables-in-a-running-task-sequence) |