---
layout: Conceptual
title: CCM_Policy_Policy Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_policy-client-wmi-class
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
description: A client Windows Management Instrumentation class that defines a policy object for a client policy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ca348a78-fc57-0a72-9fa5-5d750ac87c96
document_version_independent_id: 44b2dff2-9895-67d3-93cb-edac22887cdb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_policy-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_policy-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_policy-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: af8ca0b7-d6ec-dd0f-f029-f547d205199b
---

# CCM_Policy_Policy Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Policy` class is a client Windows Management Instrumentation (WMI) class that defines a policy object for a client policy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Policy : CCM_Policy_Config
{
      String DownloadSource;
      String PolicyCookie;
      String PolicyHash;
      String PolicyID;
      CCM_Policy_Rule PolicyRules[];
      String PolicySource;
      String PolicyState;
      String PolicyVersion;
};
```

## Methods

The `CCM_Policy_Policy` class doesn't define any methods.

## Properties

`DownloadSource` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Location from which the policy is downloaded.

`PolicyCookie` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Arbitrary data used by the source authority.

`PolicyHash` Data type: `String`

Access type: Read/Write

Qualifiers: None

Reserved.

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy object.

`PolicyRules` Data type: `CCM_Policy_Rule` Array

Access type: Read/Write

Qualifiers: None

Array of [CCM_Policy_Rule Client WMI Class](ccm_policy_rule-client-wmi-class) objects describing rules reflecting actions of the policy object. Set this property to NULL if the policy object contains no actions.

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Source authority of the policy object.

`PolicyState` Data type: `String`

Access type: Read/Write

Qualifiers: [ToInstance]

Current state of the policy object. Possible values are:

| Value | Description |
| --- | --- |
| NULL | The policy object is inactive and hasn't been downloaded. This is the default value. |
| DownloadPending | The evaluator has determined that the policy object needs to be applied and should be downloaded. This is a temporary state used during the evaluation process. |
| DownloadStarted | The policy object has been requested from the management point and is in the process of being downloaded. |
| DownloadComplete | The policy object has finished downloading from the management point but hasn't been compiled into WMI yet. |
| Inactive | The policy object is downloaded and compiled, but has no active assignments. |
| Applied | The policy object is currently active, but pending revaluation. This is a temporary state used during the evaluation process. If the evaluation determines that the policy object should no longer be active, its actions must be revoked. |
| ApplyPending | The policy object is currently inactive, but now has active assignments and actions that should be applied. This is a temporary state used during the evaluation process. |
| Active | The policy object is currently active and has been applied. |
| NotApplicable | The policy object isn't applicable.  This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Version of the policy object.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).