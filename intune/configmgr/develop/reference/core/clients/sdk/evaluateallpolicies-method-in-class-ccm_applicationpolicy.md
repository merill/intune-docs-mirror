---
layout: Conceptual
title: EvaluateAllPolicies Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/evaluateallpolicies-method-in-class-ccm_applicationpolicy
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
description: A Windows Management Instrumentation class method that evaluates all policies.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d951d63b-703d-2666-c616-7565586f7156
document_version_independent_id: 429aee71-5b77-7ee2-c963-1c1e62d7d1ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/evaluateallpolicies-method-in-class-ccm_applicationpolicy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/evaluateallpolicies-method-in-class-ccm_applicationpolicy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/evaluateallpolicies-method-in-class-ccm_applicationpolicy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fc4b0eaf-378c-e945-0b21-586dc295490a
---

# EvaluateAllPolicies Method - Configuration Manager | Microsoft Learn

The `EvaluateAllPolicies` Windows Management Instrumentation (WMI) class method in Configuration Manager that evaluated all policies.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 EvaluateAllPolicies
{
    [IN]    Boolean IsEnforceAction
    [OUT]   String JobIdUser
    [OUT]   String JobIdMachine
};
```

## Parameters

`IsEnforceAction` Data type: `Boolean`

Qualifiers: [id("0"), in]

`True` if the action is enforced.

`JobIdUser` Data type: `String`

Qualifiers: [id("1"), out]

Job identifier of a user policy.

`JobIdMachine` Data type: `String`

Qualifiers: [id("2"), out]

Job identifier of a machine policy.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).