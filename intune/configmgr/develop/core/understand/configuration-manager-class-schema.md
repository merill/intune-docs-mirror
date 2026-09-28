---
layout: Conceptual
title: Configuration Manager Class Schema - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-class-schema
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
description: Learn how to use Windows Management Instrumentation (WMI) classes that represent the objects in SMS as templates for managed objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 822a2200-1178-c210-b9a3-8caa3ed9b9da
document_version_independent_id: b817bf3f-3abb-97c2-3181-11685846c688
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-class-schema.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-class-schema
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-class-schema.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ba5b9d23-b502-25a8-ac47-d31137d5e3bc
---

# Configuration Manager Class Schema - Configuration Manager | Microsoft Learn

The Systems Management Server (SMS) class schema is a set of Windows Management Instrumentation (WMI) classes that represent the objects in SMS. Each SMS class is a template for a managed object and all instances of the object use the template. Classes can contain properties and methods: the properties describe the class data and the methods typically perform data management for the class.

## Class categories

The following table describes the categories of classes and how the classes are used.

| Category | Description |
| --- | --- |
| Server | Classes supported on servers running SMS. |
| Advanced Client | Classes supported on SMS Advanced Clients. |