---
layout: Conceptual
title: SMS_G_SYSTEM_AmPolicyStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_g_system_ampolicystatus-server-wmi-class
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
description: The SMS_G_SYSTEM_AmPolicyStatus Windows Management Instrumentation class is an SMS Provider server class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 56c710bd-8d6f-8e6e-7bd4-40bf10457750
document_version_independent_id: 3318e978-d5a8-733b-2e45-3ab8ed9305fd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_g_system_ampolicystatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_g_system_ampolicystatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_g_system_ampolicystatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 30671a2c-5102-81e9-9ccd-09a85ac7dff0
---

# SMS_G_SYSTEM_AmPolicyStatus Class - Configuration Manager | Microsoft Learn

The `SMS_G_SYSTEM_AmPolicyStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_SYSTEM_AmPolicyStatus : SMS_G_System
{
    String AssignmentUniqueID;
    String CollectionName;
    String Error;
    UInt32 ErrorCode;
    UInt32 ID;
    DateTime LastUpdateTime;
    String Name;
    UInt32 PolicyType;
    UInt32 Priority;
    UInt32 ResourceID;
    UInt32 State;
    String UniqueID;
};
```

## Methods

The `SMS_G_SYSTEM_AmPolicyStatus` class does not define any methods.

## Properties

`AssignmentUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique identifier for customized policy. For default policy, the value is always 'AntimalwareEx Agent'.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection. NULL for default policy as it's not targeted to any collection (but the whole site).

`Error` Data type: `String`

Access type: Read/Write

Qualifiers: none

The description of error when applying the policy on this computer.

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The error code when applying the policy on this computer.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy identifier. 0 for the default policy.

`LastUpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last message update time.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Policy name.

`PolicyType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy type. Possible values are:

| Value | Policy type |
| --- | --- |
| 1 | Default AM Policy |
| 2 | Customized AM Policy |

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy priority. 10000 for the default policy as it's always the lowest priority.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Client resource identifier.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The state of this policy on this computer.

| Value | Policy state |
| --- | --- |
| 1 | Success |
| 2 | Failure |

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for the policy.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).