---
layout: Conceptual
title: FormatModuleMessage Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/formatmodulemessage-method
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
description: Learn how to resolve status messages in Srvmsgs.dll, Provmsgs.dd, and Climmsgs.dll using FormatModuleMessage method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 86cad5b3-8758-b829-dbc8-8e7f26a99deb
document_version_independent_id: 113dacce-b6f6-3696-d25c-26d6d5018a4b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/formatmodulemessage-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/formatmodulemessage-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/formatmodulemessage-method.md
cmProducts: []
platformId: 8723632c-c3f2-f9dd-dfa8-fecdda45d29c
---

# FormatModuleMessage Method - Configuration Manager | Microsoft Learn

The `FormatModuleMessage` method, in Configuration Manager, resolves Configuration Manager status messages in Srvmsgs.dll, Provmsgs.dll, and Climmsgs.dll.

## Syntax

```
[VBScript]
SMSFormatMessageCtl.FormatModuleMessage
```

#### Parameters

`ModuleName` Data type: `string`

Name of the module to load. The name can be Srvmsgs.dll, Provmsgs.dll, or Climmsgs.dll.

`MessageID` Data type: `int`

Message ID logically ORed with the severity.

`InsertionStrings` Data type: `object`

Optional insertion strings.

## Return Values

A string.

## Remarks

`FormatModuleMessage` loads a string that is specified by `MessageID` from a message resource in the `ModuleName` module and inserts the supplied strings.

If insertion strings aren't passed in, the message is returned without them. Insertion strings are an optional parameter. When retrieving the messages from the Configuration Manager database, you should OR the severity with the `MessageID` parameter. You should also keep the object alive between calls to `FormatModuleMessage` because the object caches module handles. Doing this saves an extra call to `LoadLibrary`.

## Requirements

FormatMessageCtl.dll.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).