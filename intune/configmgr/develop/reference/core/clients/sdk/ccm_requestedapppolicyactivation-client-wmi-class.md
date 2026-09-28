---
layout: Conceptual
title: CCM_RequestedAppPolicyActivation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_requestedapppolicyactivation-client-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how the CCM_RequestedAppPolicy Activation class represents a requested application policy activation.
locale: en-us
document_id: f77a2c97-9325-a753-ebbf-e6902df8b6e4
document_version_independent_id: 514de6b4-fa2d-1f6a-febf-9987ac068c82
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_requestedapppolicyactivation-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_requestedapppolicyactivation-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_requestedapppolicyactivation-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 13991409-d955-fc13-bf9f-8f193829f9cd
---

# CCM_RequestedAppPolicyActivation Class - Configuration Manager | Microsoft Learn

The `CCM_RequestedAppPolicyActivation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a requested application policy activation.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_RequestedAppPolicyActivation :
{
    UInt32 ActivationAction;
    String AppId;
    DateTime DateRequested;
    Boolean IsComplete;
    String PolicyId;
    String Revision;
    String UserSID;
};
```

## Methods

The following table lists the methods in the `CCM_RequestedAppPolicyActivation` class.

- [QueueAppPolicyActivationAction Method in Class CCM_RequestedAppPolicyActivation](queueapppolicyactivationaction-method-in-class-ccm_requestedapppolicyactivation)

## Properties

`ActivationAction` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [values]

Activation action. Possible values are:

| Value | Activation action |
| --- | --- |
| 0 | default |
| 1 | By-pass Activation |

`AppId` Data type: `String`

Access type: Read/Write

Qualifiers: none

Application identifier.

`DateRequested` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date requested.

`IsComplete` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if activation is complete.

`PolicyId` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Policy identifier.

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: none

Application revision.

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

User security identifier (SID).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).