---
layout: Conceptual
title: QueueRequestedAppPolicy Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy
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
description: In Configuration Manager, the QueueRequestedAppPolicy Windows Management Instrumentation class method that queues an application policy request.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a919309a-1470-f1b3-643d-c589a8da360a
document_version_independent_id: 1ac70227-c147-c1f1-061b-c15f6013aceb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1052f02b-5fa3-2d3e-6d23-d8fd1d0665ad
---

# QueueRequestedAppPolicy Method - Configuration Manager | Microsoft Learn

The `QueueRequestedAppPolicy` Windows Management Instrumentation (WMI) class method in Configuration Manager that queues and application policy request.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 QueueRequestedAppPolicy
{
    [IN]    String PolicyId
    [IN]    String PolicyRevision
    [IN]    String Id
    [IN]    UInt32 EnforcePreference
};
```

## Parameters

`PolicyId` Data type: `String`

Qualifiers: [id("0"), in]

Policy identifier.

`PolicyRevision` Data type: `String`

Qualifiers: [id("1"), in]

Policy revision.

`Id` Data type: `String`

Qualifiers: [id("2"), in]

Identifier.

`EnforcePreference` Data type: `UInt32`

Qualifiers: [id("3"), in]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | Non-Business Hours |
| 2 | Admin Schedule |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).