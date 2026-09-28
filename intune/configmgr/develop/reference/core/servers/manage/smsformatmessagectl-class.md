---
layout: Conceptual
title: SMSFormatMessageCtl Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsformatmessagectl-class
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
description: The SMSFormatMessageCtl class supports message formatting for the Configuration Manager status system.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7c4d0d6c-581d-efd1-55c3-7d6567b0cc23
document_version_independent_id: 567096ff-22da-2250-3460-f95aebad1b1b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/smsformatmessagectl-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/smsformatmessagectl-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/smsformatmessagectl-class.md
cmProducts: []
platformId: 793267ab-5ec3-41cc-8c96-c24f77f6d76c
---

# SMSFormatMessageCtl Class - Configuration Manager | Microsoft Learn

The `SMSFormatMessageCtl` class supports message formatting for the Configuration Manager status system.

## Methods

The following table lists the methods in `SMSFormatMessageCtl`.

| Method | Description |
| --- | --- |
| [FormatModuleMessage Method](formatmodulemessage-method) | Resolves Configuration Manager status messages in Srvmsgs.dll, Provmsgs.dll, and Climmsgs.dll. |
| [FormatModuleString Method](formatmodulestring-method) | Loads string resources out of the resource DLL. |
| [FormatSystemMessage Method](formatsystemmessage-method) | Formats a system error message by using the error code and optional insertion strings. |

## Requirements

FormatMessageCtl.dll.

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).