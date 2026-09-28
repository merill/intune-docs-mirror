---
layout: Conceptual
title: CCM_InstanceEvent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_instanceevent-client-wmi-class
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
description: The CCM_InstanceEvent Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents an instance event.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 74262b91-b8dd-7064-758f-77611d82d429
document_version_independent_id: 5460f79d-77c8-eae8-8c8f-46f5e42d0c32
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_instanceevent-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_instanceevent-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_instanceevent-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 50004c4f-9de9-e9b0-1bba-6b6b1aa65751
---

# CCM_InstanceEvent Class - Configuration Manager | Microsoft Learn

The `CCM_InstanceEvent` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an instance event.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_InstanceEvent : __ExtrinsicEvent
{
    UInt32 ActionType;
    String ClassName;
    UInt32 MessageLevel;
    UInt8 SECURITY_DESCRIPTOR[];
    UInt32 SessionID;
    String TargetInstancePath;
    UInt64 TIME_CREATED;
    String UserSID;
    String Value;
    UInt32 Verbosity;
};
```

## Methods

The `CCM_InstanceEvent` class does not define any methods.

## Properties

`ActionType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

Action type. Possible values are:

| Value | Action type |
| --- | --- |
| 1 | Update |
| 2 | Delete |
| 3 | Reboot |
| 4 | RebootCountdonwStart |
| 5 | Logoff |
| 6 | ProgramAvailable |
| 7 | ProgramDownloadProgress |
| 8 | OptionalProgramReady |
| 9 | AssignedProgramReady |
| 10 | ProgramExecuteComplete |
| 11 | UpdateAvailable |
| 12 | UpdateDeleted |
| 13 | UpdateManadatoryInstallStart |
| 14 | UpdateInstallComplete |
| 15 | InstallJobStart |
| 16 | InstallJobComplete |
| 19 | AppEvaluationStarted |
| 20 | AppEvaluationComplete |
| 21 | AppAvailable |
| 22 | AppEnforcementStarted |
| 23 | AppEnforcementProgress |
| 24 | AppEnforcementSuccess |
| 25 | AppEnforcementFailure |
| 26 | AppRemoved |

`ClassName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Event target class.

`MessageLevel` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

Message level. Possible values are:

| Value | Message level |
| --- | --- |
| 0 | Informational |
| 1 | Warning |
| 2 | Error |

`SECURITY_DESCRIPTOR` Data type: `UInt8 Array`

Access type: Read/Write

Qualifiers: none

Security descriptor.

`SessionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

User logon session identifier.

`TargetInstancePath` Data type: `String`

Access type: Read/Write

Qualifiers: none

Event target instance path.

`TIME_CREATED` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

Time created.

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: none

User identifier (SID).

`Value` Data type: `String`

Access type: Read/Write

Qualifiers: none

Value for an event.

`Verbosity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

Verbosity. Possible values are:

| Value | Verbosity |
| --- | --- |
| 10 | Low |
| 20 | Medium\_Low |
| 30 | Medium |
| 40 | Medium\_High |
| 50 | High |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).