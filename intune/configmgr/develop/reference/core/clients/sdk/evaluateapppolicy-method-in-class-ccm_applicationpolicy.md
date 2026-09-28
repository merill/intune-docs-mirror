---
layout: Conceptual
title: EvaluateAppPolicy Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/evaluateapppolicy-method-in-class-ccm_applicationpolicy
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
description: Learn how the EvaluateAppPolicy Windows Management Instrumentation (WMI) class method, in Configuration Manager, that evaluates application policy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: da9e85e6-e2fa-6f0d-2066-3a57cf9fd4a4
document_version_independent_id: e8dad645-eb5e-cd75-6220-7b4226bf143f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/evaluateapppolicy-method-in-class-ccm_applicationpolicy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/evaluateapppolicy-method-in-class-ccm_applicationpolicy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/evaluateapppolicy-method-in-class-ccm_applicationpolicy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 45cb812d-3794-04b7-7fbf-35c486e2f2ab
---

# EvaluateAppPolicy Method - Configuration Manager | Microsoft Learn

The `EvaluateAppPolicy` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that evaluates application policy.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 EvaluateAppPolicy
{
    [IN]    String PolicyId
    [IN]    String PolicyRevision
    [IN]    Boolean IsMachineTarget
    [IN]    String Priority
    [IN]    Boolean IsEnforceAction
    [IN]    String MTCToken
    [IN]    String SDKCallerId
    [OUT]   String JobId
};
```

## Parameters

`PolicyId` Data type: `String`

Qualifiers: [id("0"), in]

Policy identifier.

`PolicyRevision` Data type: `String`

Qualifiers: [id("1"), in]

Policy revision.

`IsMachineTarget` Data type: `Boolean`

Qualifiers: [id("2"), in]

`True` if this is a device targeted application.

`Priority` Data type: `String`

Qualifiers: [id("3"), in, valuemap]

Priority. Possible values are:

| Value |
| --- |
| Foreground |
| High |
| Normal |
| Low |

`IsEnforceAction` Data type: `Boolean`

Qualifiers: [id("4"), in]

`True` if the action will be enforced.

`MTCToken` Data type: `String`

Qualifiers: [id("5"), in]

MTC token.

`SDKCallerId` Data type: `String`

Qualifiers: [id("6"), in]

SDK caller identifier.

`JobId` Data type: `String`

Qualifiers: [id("7"), out]

Job identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).