---
layout: Conceptual
title: GetEvaluationState Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getevaluationstate-method-in-class-ccm_applicationpolicy
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
description: The GetEvaluationState Windows Management Instrumentation (WMI) class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1606084b-b5b5-f352-a591-3d61be382742
document_version_independent_id: 66f999e7-053d-e086-83a3-9b332df6eaf3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getevaluationstate-method-in-class-ccm_applicationpolicy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getevaluationstate-method-in-class-ccm_applicationpolicy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getevaluationstate-method-in-class-ccm_applicationpolicy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 60483fb6-0da0-b5bf-9775-02abaf612dae
---

# GetEvaluationState Method - Configuration Manager | Microsoft Learn

The `GetEvaluationState` Windows Management Instrumentation (WMI) class method in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetEvaluationState
{
    [IN]    String PolicyId
    [IN]    String PolicyRevision
    [IN]    Boolean IsMachineTarget
    [OUT]   Object PolicyEvalState
    [OUT]   Object AppEvalState
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

`true` if it's a device targeted application.

`PolicyEvalState` Data type: `CCM_EvaluationState`

Qualifiers: [id("3"), out]

Policy evaluation state.

`AppEvalState` Data type: `CCM_EvalutationState`

Qualifiers: [id("4"), out]

Application evaluation state.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).