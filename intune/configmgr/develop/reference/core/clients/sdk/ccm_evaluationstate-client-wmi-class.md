---
layout: Conceptual
title: CCM_EvaluationState Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_evaluationstate-client-wmi-class
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
description: The CCM_EvaluationState WMI class is an SMS Provider server class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0ea38790-2181-8e75-5190-705ac3d1bbc8
document_version_independent_id: d9efde12-86b1-d718-bfe7-9bf9f8057c8e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_evaluationstate-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_evaluationstate-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_evaluationstate-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c8d3c934-ed2f-7361-300a-d9760d893dab
---

# CCM_EvaluationState Class - Configuration Manager | Microsoft Learn

The `CCM_EvaluationState` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_EvaluationState :
{
    UInt32 ErrorCode;
    UInt32 EvaluationState;
    UInt32 PercentComplete;
};
```

## Methods

The `CCM_EvaluationState` class doesn't define any methods.

## Properties

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Error code.

`EvaluationState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Evaluation state. Possible values are:

| Evaluation State Value | Description |
| --- | --- |
| 0 | No state information is available. |
| 1 | Application is enforced to desired/resolved state. |
| 2 | Application isn't required on the client. |
| 3 | Application is available for enforcement (install or uninstall based on resolved state). Content may/may not have been downloaded. |
| 4 | Application last failed to enforce (install/uninstall). |
| 5 | Application is currently waiting for content download to complete. |
| 6 | Application is currently waiting for content download to complete. |
| 7 | Application is currently waiting for its dependencies to download. |
| 8 | Application is currently waiting for a service (maintenance) window. |
| 9 | Application is currently waiting for a previously pending reboot. |
| 10 | Application is currently waiting for serialized enforcement. |
| 11 | Application is currently enforcing dependencies. |
| 12 | Application is currently enforcing. |
| 13 | Application install/uninstall enforced and soft reboot is pending. |
| 14 | Application installed/uninstalled and hard reboot is pending. |
| 15 | Update is available but pending installation. |
| 16 | Application failed to evaluate. |
| 17 | Application is currently waiting for an active user session to enforce. |
| 18 | Application is currently waiting for all users to sign out. |
| 19 | Application is currently waiting for a user sign in. |
| 20 | Application in progress, waiting for retry. |
| 21 | Application is waiting for presentation mode to be switched off. |
| 22 | Application is pre-downloading content (downloading outside of install job). |
| 23 | Application is pre-downloading dependent content (downloading outside of install job). |
| 24 | Application download failed (downloading during install job). |
| 25 | Application pre-downloading failed (downloading outside of install job). |
| 26 | Download success (downloading during install job). |
| 27 | Post-enforce evaluation. |
| 28 | Waiting for network connectivity. |

`PercentComplete` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Percent complete.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).