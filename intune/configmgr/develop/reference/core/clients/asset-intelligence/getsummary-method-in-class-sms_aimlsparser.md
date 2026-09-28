---
layout: Conceptual
title: GetSummary Method in Class SMS_AIMLSParser - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aimlsparser
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
description: The GetSummary Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves the counts of imported Microsoft and non-Microsoft license count.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 65ddb346-2ba1-9938-40af-f476595c8af7
document_version_independent_id: 3265e87c-e06e-86e3-47cd-b19205dbd068
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aimlsparser.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aimlsparser
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aimlsparser.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 260e7ee9-1b7b-ae69-8778-4f9f27cfc092
---

# GetSummary Method in Class SMS_AIMLSParser - Configuration Manager | Microsoft Learn

The `GetSummary` Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves the counts of imported Microsoft License count and non-Microsoft license count.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 MVLSCount;
     UInt32 NonMSLicenseCount;
);
```

#### Parameters

`MVLSCount` Data type: `UInt32`

Qualifiers: [out]

Returns the Microsoft License count.

`NonMSLicenseCount` Data type: `UInt32`

Qualifiers: [out]

Returns the non-Microsoft License count.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).