---
layout: Conceptual
title: GetSummary Method in Class SMS_AISoftwareList - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aisoftwarelist
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
description: A Windows Management Instrumentation class method that returns a summary count of each of the states defined by the SMS_AISoftwareList WMI class records State property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8e7cac1a-8f44-acbf-93ce-65304bfd838b
document_version_independent_id: 93edd0e9-11d2-bde5-4560-87cc9fec7114
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aisoftwarelist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aisoftwarelist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aisoftwarelist.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e884103-5159-66e2-960a-b2031d601f6e
---

# GetSummary Method in Class SMS_AISoftwareList - Configuration Manager | Microsoft Learn

The `GetSummary` Windows Management Instrumentation (WMI) class method, in Configuration Manager, returns a summary count of each of the states defined by the `SMS_AISoftwareList` WMI class records `State` property.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 Validated,
     UInt32 UserDefined,
     UInt32 Pending,
     UInt32 Updatable,
     UInt32 Uncategorized
);
```

#### Parameters

`Validated` Data type: `UInt32`

Qualifiers: [out]

Count of software titles with the state `Validated`.

`UserDefined` Data type: `UInt32`

Qualifiers: [out]

Count of software titles with the state `User Defined`.

`Pending` Data type: `UInt32`

Qualifiers: [out]

Count of software titles with the state `Pending`.

`Updatable` Data type: `UInt32`

Qualifiers: [out]

Count of software titles with the state `Updatable`.

`Uncategorized` Data type: `UInt32`

Qualifiers: [out]

Count of software titles with the state `Uncategorized`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).