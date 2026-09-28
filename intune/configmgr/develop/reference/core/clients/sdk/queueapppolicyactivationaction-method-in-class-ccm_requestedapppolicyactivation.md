---
layout: Conceptual
title: QueueAppPolicyActivationAction Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/queueapppolicyactivationaction-method-in-class-ccm_requestedapppolicyactivation
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
description: The QueueAppPolicyActivationAction WMI class method queues an application policy activation action.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8d2aaada-f627-9674-feb8-81600cb9e79f
document_version_independent_id: 4c2325f3-2d4b-c56f-2eab-52ea81cb5ab3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/queueapppolicyactivationaction-method-in-class-ccm_requestedapppolicyactivation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/queueapppolicyactivationaction-method-in-class-ccm_requestedapppolicyactivation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/queueapppolicyactivationaction-method-in-class-ccm_requestedapppolicyactivation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 80d24af9-c071-1224-47d8-61afcd7a9202
---

# QueueAppPolicyActivationAction Method - Configuration Manager | Microsoft Learn

The `QueueAppPolicyActivationAction` Windows Management Instrumentation (WMI) class method in Configuration Manager that queues an application policy activation action.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 QueueAppPolicyActivationAction
{
    [IN]    String PolicyId
    [IN]    String PolicyRevision
    [IN]    String Id
    [IN]    UInt32 ActivationAction
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

Application identifier.

`ActivationAction` Data type: `UInt32`

Qualifiers: [id("3"), in]

Activation action. Possible values are:

| Value | Activation action |
| --- | --- |
| 0 | default |
| 1 | By-pass activation. |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).