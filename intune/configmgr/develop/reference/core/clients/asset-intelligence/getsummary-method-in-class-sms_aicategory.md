---
layout: Conceptual
title: GetSummary Method in Class SMS_AICategory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aicategory
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
description: The GetSummary Windows Management Instrumentation class method provides a summary count of all the categories, families, and tags used by Asset Intelligence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f34e6b9b-7dbe-5de9-fb16-6e52b0426fda
document_version_independent_id: 76ccbdb9-1732-8052-5ee3-f46e95390b60
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aicategory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aicategory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aicategory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0596f236-5772-0b13-2aec-5ae37498aa70
---

# GetSummary Method in Class SMS_AICategory - Configuration Manager | Microsoft Learn

The `GetSummary` Windows Management Instrumentation (WMI) class method, in Configuration Manager, provides a summary count of all the categories, families, and tags used by Asset Intelligence.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 ValidatedCategory,
     UInt32 UserDefinedCategory,
     UInt32 ValidatedFamily,
     UInt32 UserDefinedFamily,
     UInt32 UserDefinedTags
);
```

#### Parameters

`ValidatedCategory` Data type: `UInt32`

Qualifiers: [out]

Count of Microsoft-defined categories.

`UserDefinedCategory` Data type: `UInt32`

Qualifiers: [out]

Count of user-defined categories.

`ValidatedFamily` Data type: `UInt32`

Qualifiers: [out]

Count of Microsoft-defined families.

`UserDefinedFamily` Data type: `UInt32`

Qualifiers: [out]

Count of user-defined families.

`UserDefinedTags` Data type: `UInt32`

Qualifiers: [out]

Count of all tags defined by the user.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).