---
layout: Conceptual
title: Smscstat.dll Status Message Functions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smscstat.dll-status-message-functions
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
description: In Configuration Manager, the functions defined by the Smscstat.dll dynamic-link library, report status messages that can be called by using a C interface.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 61a03c83-566e-56aa-e637-7095beb60d9e
document_version_independent_id: 1df93825-f92b-ce38-fb18-222b00276132
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/smscstat.dll-status-message-functions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/smscstat.dll-status-message-functions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/smscstat.dll-status-message-functions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: d8c84343-4eb5-209d-5457-20ec03f0625d
---

# Smscstat.dll Status Message Functions - Configuration Manager | Microsoft Learn

In Configuration Manager, the functions that are defined by the Smscstat.dll dynamic-link library, report status messages that can be called by using a C interface.

## Functions

Smscstat.dll exports the following functions.

| Term | Description |
| --- | --- |
| [AddAttributeToSMSStatusMessage Function](addattributetosmsstatusmessage-function) | Adds a single optional status message attribute ID/value pair to a status message object. |
| [CreateSMSStatusMessage Function](createsmsstatusmessage-function) | Creates a status message object. |
| [ReportSMSStatusMessage Function](reportsmsstatusmessage-function) | Submits a status message object to the Configuration Manager status system. |