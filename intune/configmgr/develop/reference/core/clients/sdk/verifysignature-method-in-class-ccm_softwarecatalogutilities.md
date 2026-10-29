---
layout: Conceptual
title: VerifySignature Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/verifysignature-method-in-class-ccm_softwarecatalogutilities
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
description: In Configuration Manager, the VerifySignature WMI class method verifies the data signature.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d6e40b3d-887b-cc62-b8ff-21cab1adc48b
document_version_independent_id: bc99403b-34b1-3139-b398-e3e53a903de8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/verifysignature-method-in-class-ccm_softwarecatalogutilities.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/verifysignature-method-in-class-ccm_softwarecatalogutilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/verifysignature-method-in-class-ccm_softwarecatalogutilities.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a83bab55-9552-d65f-61ca-a1bf1b55cad1
---

# VerifySignature Method - Configuration Manager | Microsoft Learn

The `VerifySignature` Windows Management Instrumentation (WMI) class method in Configuration Manager that verifies the data signature.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 VerifySignature
{
    [IN]    String Data
    [IN]    String DataSignature
    [IN]    String WebServiceID
    [IN]    Boolean VerifyUserAndTimestamp
    [OUT]   Boolean SignatureVerificationPassed
};
```

## Parameters

`Data` Data type: `String`

Qualifiers: [id("0"), in]

Data to verify.

`DataSignature` Data type: `String`

Qualifiers: [id("1"), in]

Data signature.

`WebServiceID` Data type: `String`

Qualifiers: [id("2"), in]

Web Service identifier.

`VerifyUserAndTimestamp` Data type: `Boolean`

Qualifiers: [id("3"), in]

`true` to verify the user and timestamp.

`SignatureVerificationPassed` Data type: `Boolean`

Qualifiers: [id("4"), out]

`true` if the data signature is valid.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).