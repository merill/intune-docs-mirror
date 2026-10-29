---
layout: Conceptual
title: InitiateClientOperation Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/initiateclientoperation-method-in-class-sms_clientoperation
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
description: In Configuration Manager, the InitiateClientOperation WMI class method initiates a client operation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4cf57d1a-f2bf-75c0-9843-a1368ad2039a
document_version_independent_id: 047a2a0f-daa6-aaf6-b65a-c284cd682acf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/initiateclientoperation-method-in-class-sms_clientoperation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/initiateclientoperation-method-in-class-sms_clientoperation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/initiateclientoperation-method-in-class-sms_clientoperation.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6058cd46-7bf2-69ca-bf9d-9632eac1a127
---

# InitiateClientOperation Method - Configuration Manager | Microsoft Learn

The `InitiateClientOperation` Windows Management Instrumentation (WMI) class method in Configuration Manager that initiates a client operation.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 InitiateClientOperation
{
    [IN]    UInt32 Type
    [IN]    String TargetCollectionID
    [IN]    UInt32 RandomizationWindow
    [IN]    UInt32 TargetResourceIDs[]
    [OUT]   UInt32 OperationID
};
```

## Parameters

`Type` Data type: `UInt32`

Qualifiers: [id("0"), in]

Type.

`TargetCollectionID` Data type: `String`

Qualifiers: [id("1"), in]

TargetCollectionID.

`RandomizationWindow` Data type: `UInt32`

Qualifiers: [id("2"), in, optional]

RandomizationWindow.

`TargetResourceIDs` Data type: `UInt32 Array`

Qualifiers: [id("3"), in, optional]

TargetResourceIDs.

`OperationID` Data type: `UInt32`

Qualifiers: [id("4"), out]

OperationID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).