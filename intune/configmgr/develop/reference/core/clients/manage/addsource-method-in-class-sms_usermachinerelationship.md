---
layout: Conceptual
title: AddSource Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/addsource-method-in-class-sms_usermachinerelationship
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: In Configuration Manager, the AddSource Windows Management Instrumentation class method adds a source for the relationship between the user and the device.
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 67ef65a1-f297-f9b1-d9b6-eb171f624e05
document_version_independent_id: 629a3930-5c0e-53b6-508f-37f3792ad55c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/addsource-method-in-class-sms_usermachinerelationship.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/addsource-method-in-class-sms_usermachinerelationship
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/addsource-method-in-class-sms_usermachinerelationship.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4cc7d522-3d2b-6394-2c6b-95cade0d65d5
---

# AddSource Method - Configuration Manager | Microsoft Learn

The `AddSource` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds a source for the relationship between the user and the device.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 AddSource(
     uint32 SourceId
);
```

#### Parameters

`SourceId` Data type: `UInt32`

Qualifiers: `[in]`

Source object identifier for dependency.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).