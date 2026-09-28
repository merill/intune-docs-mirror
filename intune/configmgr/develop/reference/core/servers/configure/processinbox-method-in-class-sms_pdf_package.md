---
layout: Conceptual
title: ProcessInBox Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/processinbox-method-in-class-sms_pdf_package
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
description: In Configuration Manager, the ProcessInBox Windows Management Instrumentation class method imports package definition files from the package definition file inbox.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b24eef77-95a8-ef88-9a55-cdbc9cc02c63
document_version_independent_id: e400a8a5-e2f0-0132-fb03-28ec41147e84
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/processinbox-method-in-class-sms_pdf_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/processinbox-method-in-class-sms_pdf_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/processinbox-method-in-class-sms_pdf_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: aab67e37-3742-2435-6a3d-38671c10722e
---

# ProcessInBox Method - Configuration Manager | Microsoft Learn

The `ProcessInBox` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports package definition files from the package definition file inbox.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ProcessInBox();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is the number of package definition files successfully loaded.

## Remarks

This method processes all .pdf and .sms files found in the \*Smsinstalldir*\Scripts\&lt;*localeid*&gt;\Pdfstore\Load inbox. Successfully processed files are then removed and placed in the package definition file store. Files that fail to load, however, remain in the load directory.

Configuration Manager uses this method at startup to load package definition file templates if the Configuration Manager tables are empty. Icons defined in the package definition file for the package or programs must exist in the load directory at the time the method is called.

When your application imports a package definition file that has the same `Name`, `Publisher`, `Version`, and `Language` properties as an existing package definition file, the existing package definition file is overwritten, including file icons and programs. The value specified by the `PDFID` parameter is retained.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).