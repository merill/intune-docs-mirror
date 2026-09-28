---
layout: Conceptual
title: Embedded Objects - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/embedded-objects
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
description: You cannot use Windows Management Instrumentation (WMI) to enumerate, query, get, or put embedded objects. You can only retrieve and store embedded objects through the parent instance.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 2903e1e4-45fd-ea2e-ad47-8ed5fe259e64
document_version_independent_id: 0a1a25f1-fe97-8494-1548-8ee010b83623
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/embedded-objects.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/embedded-objects
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/embedded-objects.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e5e14c48-63f7-1930-36d4-4123e18faa94
---

# Embedded Objects - Configuration Manager | Microsoft Learn

Configuration Manager embedded objects do not exist by themselves in the Common Information Model (CIM) repository — they exist within other objects. As a result, you cannot use Windows Management Instrumentation (WMI) to enumerate, query, get, or put embedded objects. You can only retrieve and store embedded objects through the parent instance.

Embedded objects are commonly used when accessing the site control file. In this case, special embedded objects, such as properties and property lists are used.

When a class or method contains an embedded object of an abstract type, such as `SMS_ScheduleToken`, you store and retrieve classes that are inherited from it. For example, instead of using `SMS_ScheduleToken`, you use one of the embedded objects inherited from it, such as `SMS_ST_RecurWeekly`.