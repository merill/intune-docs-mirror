---
layout: Conceptual
title: GetSuppressComputerActivityInPresentationMode Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getsuppresscomputeractivityinpresentationmode-method
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
description: Article outlining the use of the GetSuppressComputerActivityInPresentationMode in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 02549398-0f76-9564-5a58-e083d7b3c7d5
document_version_independent_id: 0bff42cb-a9bf-779d-c5c3-1435b1e05d7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getsuppresscomputeractivityinpresentationmode-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getsuppresscomputeractivityinpresentationmode-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getsuppresscomputeractivityinpresentationmode-method.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: dc304cff-0ad1-e523-b7de-0df946d94201
---

# GetSuppressComputerActivityInPresentationMode Method - Configuration Manager | Microsoft Learn

The `GetSuppressComputerActivityInPresentationMode` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that gets the value for `SuppressComputerActivityInPresentationMode`

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetSuppressComputerActivityInPresentationMode
{
    [OUT]   Boolean SuppressComputerActivityInPresentationMode
};
```

## Parameters

`SuppressComputerActivityInPresentationMode` Data type: `Boolean`

Qualifiers: [id("0"), out]

`true` to suppress computer activity in presentation mode.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).