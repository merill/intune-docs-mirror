---
layout: Conceptual
title: GetPolicyState Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getpolicystate-method-in-class-ccm_softwarecatalogutilities
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
description: A Windows Management Instrumentation (WMI) class method that returns the state of a policy object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a8b606a2-a408-02dd-77a6-a305d4e9e659
document_version_independent_id: 301f8d40-76db-1d69-6541-a6fdf4761c4e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getpolicystate-method-in-class-ccm_softwarecatalogutilities.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getpolicystate-method-in-class-ccm_softwarecatalogutilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getpolicystate-method-in-class-ccm_softwarecatalogutilities.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3279541b-f884-7924-515d-96f0173e0c31
---

# GetPolicyState Method - Configuration Manager | Microsoft Learn

The `GetPolicyState` Windows Management Instrumentation (WMI) class method in Configuration Manager that returns the state of a policy object.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetPolicyState
{
    [IN]    String Id
    [OUT]   UInt32 Status
    [OUT]   UInt32 State
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: [id("0"), in]

Unique ID of the policy object.

`Status` Data type: `UInt32`

Qualifiers: [id("1"), out]

Current status.

`State` Data type: `UInt32`

Qualifiers: [id("2"), out]

Current state of the policy object. Possible values are:

| Value | State |
| --- | --- |
| NULL | The policy object is inactive and hasn't been downloaded. This value is the default value. |
| DownloadPending | The evaluator determines that the policy object needs to be applied and should be downloaded. This state is a temporary one used during the evaluation process. |
| DownloadStarted | The policy object has been requested from the management point and is in the process of being downloaded. |
| DownloadComplete | The policy object finished downloading from the management point but hasn't been compiled into WMI yet. |
| Inactive | The policy object is downloaded and compiled, but has no active assignments. |
| Applied | The policy object is currently active, but pending revaluation. This state is a temporary one used during the evaluation process. If the evaluation determines that the policy object should no longer be active, its actions must be revoked. |
| ApplyPending | The policy object is currently inactive, but now has active assignments and actions that should be applied. This state is a temporary one used during the evaluation process. |
| Active | The policy object is currently active and has been applied. |
| NotApplicable | The policy object isn't applicable.  This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).