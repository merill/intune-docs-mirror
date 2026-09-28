---
layout: Conceptual
title: FormatModuleString Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/formatmodulestring-method
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
description: The FormatModuleString method, in Configuration Manager, loads string resources from the resource DLL.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bab36a13-70e4-a991-e1ff-b819bf131abb
document_version_independent_id: a09d2be8-5982-7bfb-af0a-0e83967743f2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/formatmodulestring-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/formatmodulestring-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/formatmodulestring-method.md
cmProducts: []
platformId: 24920f42-a407-d06f-fac0-b6c1d224ad03
---

# FormatModuleString Method - Configuration Manager | Microsoft Learn

The `FormatModuleString` method, in Configuration Manager, loads string resources from the resource DLL.

## Syntax

```
[VBScript]
SMSFormatMessageCtl.FormatModuleString
```

#### Parameters

`ModuleName` Data type: `string`

Name of the module to load. The name can be Srvmsgs.dll, Provmsgs.dll, or Climmsgs.dll.

`MessageID` Data type: `int`

Message ID " combined by using the bitwise OR operation with the severity.

`InsertionStrings` Data type: `object`

Optional list of insertion strings.

## Return Value

A string.

## Remarks

`FormatModuleString` loads a string that is specified by `MessageID` from a string resource in the `ModuleName` module and inserts the supplied strings.

## Requirements

FormatMessageCtl.dll.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).