---
layout: Conceptual
title: CCM_CIEvaluationJob Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_cievaluationjob-client-wmi-class
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
description: The CCM_CIEvaluationJob Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a configuration item evaluation job.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8f30ed0e-5eb7-f5f5-f750-b0fbe81f3c68
document_version_independent_id: b2fca4e7-5157-524a-27e3-ee081b51767f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_cievaluationjob-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_cievaluationjob-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_cievaluationjob-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ee0590d8-3d48-8de4-b6ca-4331004245f5
---

# CCM_CIEvaluationJob Class - Configuration Manager | Microsoft Learn

The `CCM_CIEvaluationJob` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a configuration item evaluation job.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_CIEvaluationJob :
{
    String CIAgentJobId;
    UInt32 ErrorCode;
    String Id;
    Boolean IsMachineTarget;
    Boolean IsRebootRequired;
    String JobState;
    DateTime LastModifiedTime;
    String OwnerSID;
    String Type;
    String UserSID;
};
```

## Methods

The `CCM_CIEvaluationJob` class doesn't define any methods.

## Properties

`CIAgentJobId` Data type: `String`

Access type: Read/Write

Qualifiers: none

CI agent job identifier.

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Error code.

`Id` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier.

`IsMachineTarget` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is a device targeted application.

`IsRebootRequired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if a reboot is required.

`JobState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Job state. Possible values are:

| Value |
| --- |
| Idle |
| Evaluating |
| Success |
| Error |
| CanceledOrDeleted |

`LastModifiedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last modified time.

`OwnerSID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Owner identifier (SID).

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: [valuemap]

Job type. Possible values are:

| Value |
| --- |
| DesiredConfiguration |
| ApplicationManagement |
| SoftwareUpdates |

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: none

User identifier (SID).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).