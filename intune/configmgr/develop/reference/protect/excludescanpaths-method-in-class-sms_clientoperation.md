---
layout: Conceptual
title: ExcludeScanPaths Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/excludescanpaths-method-in-class-sms_clientoperation
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
description: Learn how to exclude scan paths from all members in a specified collection using the ExcludeScanPaths class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e503e402-5e6f-526d-479f-79c8a47c72a9
document_version_independent_id: bdda8499-3719-04c5-c5b4-34afc10e8d4c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/excludescanpaths-method-in-class-sms_clientoperation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/excludescanpaths-method-in-class-sms_clientoperation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/excludescanpaths-method-in-class-sms_clientoperation.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 8663efb1-1e10-a4a3-3a29-44b69a812768
---

# ExcludeScanPaths Method - Configuration Manager | Microsoft Learn

The `ExcludeScanPaths` Windows Management Instrumentation (WMI) class method in Configuration Manager that excludes scan paths from all members in specified collection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 ExcludeScanPaths
{
    [IN]    UInt64 ThreatID
    [IN]    String ExclusionSettingsUniqueID
    [IN]    String ExcludedPaths[]
    [IN]    String TargetCollectionID
    [OUT]   UInt32 OperationID
};
```

## Parameters

`ThreatID` Data type: `UInt64`

Qualifiers: [id("0"), in]

ThreatID.

`ExclusionSettingsUniqueID` Data type: `String`

Qualifiers: [id("1"), in]

ExclusionSettingsUniqueID.

`ExcludedPaths` Data type: `String Array`

Qualifiers: [id("2"), in]

ExcludedPaths.

`TargetCollectionID` Data type: `String`

Qualifiers: [id("3"), in]

TargetCollectionID.

`OperationID` Data type: `UInt32`

Qualifiers: [id("4"), out]

OperationID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).