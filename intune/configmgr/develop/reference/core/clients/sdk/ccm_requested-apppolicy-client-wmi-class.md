---
layout: Conceptual
title: CCM_Requested AppPolicy Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_requested-apppolicy-client-wmi-class
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
description: Learn how to represent an application policy request with CCM_RequestedAppPolicy in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b3056243-830a-6501-7beb-07808e55445a
document_version_independent_id: 5cc602db-dbea-f4f8-2316-f03a87726ea4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_requested-apppolicy-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_requested-apppolicy-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_requested-apppolicy-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6f52f6a3-3692-fa71-7246-2ee2480faf7b
---

# CCM_Requested AppPolicy Class - Configuration Manager | Microsoft Learn

The `CCM_RequestedAppPolicy` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an application policy request.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_RequestedAppPolicy :
{
    String AppId;
    DateTime DateRequested;
    UInt32 EnforcePreference;
    Boolean IsComplete;
    Boolean IsRebootIfNeeded;
    Boolean IsSlowInstallRequest;
    String PolicyId;
    UInt32 RequestedActions;
    String Revision;
    String UserSID;
};
```

## Methods

The following table lists the methods in the `CCM_RequestedAppPolicy` class.

- [QueueRequestedAppPolicy Method in Class CCM_RequestedAppPolicy](queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy)

## Properties

`AppId` Data type: `String`

Access type: Read/Write

Qualifiers: none

Application identifier.

`DateRequested` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date requested.

`EnforcePreference` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [values]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | Non-business Hours |
| 2 | Admin Schedule |

`IsComplete` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if application request is complete.

`IsRebootIfNeeded` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if a reboot is needed.

`IsSlowInstallRequest` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is an installation over a slow link.

`PolicyId` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Policy identifier.

`RequestedActions` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Requested actions.

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: none

Revision.

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

User security identifier (SID).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).