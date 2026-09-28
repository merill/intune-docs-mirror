---
layout: Conceptual
title: SMS_ClientAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_clientaction-server-wmi-class
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
description: The SMS_ClientAction Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the client action.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cc90c066-3999-a6fb-f28b-4085dd52b947
document_version_independent_id: 2d1a89b8-e6ea-2735-3e34-d6cc892f34ee
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_clientaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_clientaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_clientaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 99a27fad-f8ba-abe9-75e8-f8bdf7caad35
---

# SMS_ClientAction Class - Configuration Manager | Microsoft Learn

The `SMS_ClientAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the client action.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientAction :
{
    UInt32 DwordValue;
    UInt32 ID;
    UInt32 LinkedObjectType;
    String LinkedObjectUniqueID;
    UInt32 State;
    String StringValue;
    String StringValues[];
    String TargetObjectID;
    UInt32 TargetObjectType;
    UInt32 Type;
    String UniqueID;
};
```

## Methods

The `SMS_ClientAction` class does not define any methods.

## Properties

`DwordValue` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The DWORD string value of action.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier for this instance.

`LinkedObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The linked object type. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | AM Policy |

`LinkedObjectUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique ID of the linked object.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

State of the client action. Possible values are:

| Value | Action state |
| --- | --- |
| 0 | Inactive |
| 1 | Active |
| 2 | Decommission |

`StringValue` Data type: `String`

Access type: Read/Write

Qualifiers: none

The parameter for the client action, for instance the threat name to restore.

`StringValues` Data type: `String` Array

Access type: Read/Write

Qualifiers: none

The parameter for the client action (in string array), for instance the excluded scan paths.

`TargetObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The unique identifier of the target object.

`TargetObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The target object type. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | Threat |

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Action type. Possible values are:

| Value | Action type |
| --- | --- |
| 1 | Full Scan |
| 2 | Quick Scan |
| 3 | Download Definition |
| 4 | Evaluate Software Update |
| 5 | Exclude Scan Path |
| 6 | Override Default Action |
| 7 | Restore Quarantine Items |
| 8 | Request Policy Now |

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for this instance.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).