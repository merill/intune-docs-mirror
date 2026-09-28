---
layout: Conceptual
title: FormatSystemMessage Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/formatsystemmessage-method
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
description: Learn how the FormatSystemMessage method, in Configuration Manager, formats a system error message by using the error code and optional insertion strings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b951dda0-e4b2-a0b9-9128-b43a79e607eb
document_version_independent_id: c5eaf286-af3a-747a-1b03-93d5f4bc204c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/formatsystemmessage-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/formatsystemmessage-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/formatsystemmessage-method.md
cmProducts: []
platformId: 0f50b080-591e-ba4e-5805-120d35c00a70
---

# FormatSystemMessage Method - Configuration Manager | Microsoft Learn

The `FormatSystemMessage` method, in Configuration Manager, formats a system error message by using the error code and optional insertion strings.

## Syntax

```
[VBScript]
SMSFormatMessageCtl.FormatSystemMessage
```

#### Parameters

`MessageID` Data type: `int`

Error message ID.

`InsertionStrings` Data type: `object`

Optional list of insertion strings.

## Return Value

A string.

## Requirements

FormatMessageCtl.dll.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).