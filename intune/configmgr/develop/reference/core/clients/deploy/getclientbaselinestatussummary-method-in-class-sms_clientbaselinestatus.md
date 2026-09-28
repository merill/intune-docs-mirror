---
layout: Conceptual
title: GetClientBaselineStatusSummary Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/getclientbaselinestatussummary-method-in-class-sms_clientbaselinestatus
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
description: The GetClientBaselineStatusSummary WMI class method gets baseline status summary information by BaselineType and CollectionID.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d0e50dbb-7e72-d3a9-bbe0-3c5431ac052d
document_version_independent_id: df2e7fa9-0b42-83c7-654a-49b16f80f410
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/getclientbaselinestatussummary-method-in-class-sms_clientbaselinestatus.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/getclientbaselinestatussummary-method-in-class-sms_clientbaselinestatus
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/getclientbaselinestatussummary-method-in-class-sms_clientbaselinestatus.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ade54bea-f729-e33a-6024-7a5f99ca07b9
---

# GetClientBaselineStatusSummary Method - Configuration Manager | Microsoft Learn

The `GetClientBaselineStatusSummary` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets baseline status summary information by `BaselineType` and `CollectionID`.

## Syntax

```
sint32 GetClientBaselineStatusSummary(
     UInt32 BaselineType,
     String CollectionID,
     UInt32 Total,
     UInt32 Compliant,
     UInt32 InProgress,
     UInt32 NotCompliant,
     UInt32 CriticalError
);

```

#### Parameters

`BaselineType` Data type: `uint32`

Qualifiers: [in]

The client baseline type. Possible values are:

| Value | Client baseline type |
| --- | --- |
| 1 | Production |
| 2 | Staging |

`CollectionID` Data type: `String`

Qualifiers: [in]

The collection for which you want to get the baseline status summary.

`Total` Data type: `uint32`

Qualifiers: [out]

The total number of clients in the specified collection.

`Compliant` Data type: `uint32`

Qualifiers: [out]

The number of clients in the specified collection that are compliant with the baseline.

`InProgress` Data type: `uint32`

Qualifiers: [out]

The number of clients in the specified collection for which setup is in progress.

`NotCompliant` Data type: `uint32`

Qualifiers: [out]

The number of clients in the specified collection that are not compliant.

`CriticalError` Data type: `uint32`

Qualifiers: [out]

The number of clients in the specified collection that have a critical error.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).