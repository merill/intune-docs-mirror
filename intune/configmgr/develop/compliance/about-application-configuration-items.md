---
layout: Conceptual
title: About Application Configuration Items - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-application-configuration-items
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
description: Application configuration items include all the functionality of general configuration items, but their identity can be detected independently of its settings and objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 64872c49-59cf-4080-2bf1-01c111a44771
document_version_independent_id: dd7c704e-d37c-0c07-df86-76d368040b29
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/about-application-configuration-items.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/about-application-configuration-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/about-application-configuration-items.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e93f3d5f-c77d-4365-a7fb-c9f2234416c7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/62e8d07a-cc62-4934-b30b-e168a571e51d
platformId: a5bab76f-d581-e78b-7513-246b8f439f12
---

# About Application Configuration Items - Configuration Manager | Microsoft Learn

Application configuration items include all the functionality of general configuration items, but their identity can be detected independently of its settings and objects. Desired Configuration Management in Configuration Manager supports two methods for detecting the presence of an application configuration item: (1) Windows Installer package and (2) Script-based discovery. Configuration item (level) discoverability allows application configuration items to be referenced as prohibited or optional within the context of a configuration baseline.

Examples of application configuration items might include:

- Microsoft Office Professional 2003
- Microsoft Word