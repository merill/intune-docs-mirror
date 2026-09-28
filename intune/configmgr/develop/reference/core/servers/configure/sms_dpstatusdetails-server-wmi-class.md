---
layout: Conceptual
title: SMS_DPStatusDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpstatusdetails-server-wmi-class
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
description: In Configuration Manager, the SMS_DPStatusDetails WMI class is an SMS Provider server class that represents distribution point status details.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b916b121-95c8-508f-fe16-6d17bde5fcf4
document_version_independent_id: a4a71d99-3681-80ce-64d3-a34710b95e05
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_dpstatusdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_dpstatusdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_dpstatusdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36466b2a-0687-29f8-d415-3d3eb827bbca
---

# SMS_DPStatusDetails Class - Configuration Manager | Microsoft Learn

The `SMS_DPStatusDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents distribution point status details.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DPStatusDetails : SMS_BaseClass
{
    String DPName;
    SInt64 ID;
    String InsString1;
    String InsString10;
    String InsString2;
    String InsString3;
    String InsString4;
    String InsString5;
    String InsString6;
    String InsString7;
    String InsString8;
    String InsString9;
    DateTime LastStatusTime;
    UInt32 MessageCategory;
    UInt32 MessageFullID;
    UInt32 MessageID;
    UInt32 MessageSeverity;
    UInt32 MessageState;
    String NALPath;
    String PackageID;
    String SiteCode;
    SInt64 StatusMsgID;
};
```

## Methods

The `SMS_DPStatusDetails` class does not define any methods.

## Properties

`DPName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of the distribution point.

`ID` Data type: `SInt64`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Identifier for the distribution point.

`InsString1` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString10` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString2` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString3` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString4` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString5` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString6` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString7` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString8` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString9` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`LastStatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time of the status message.

`MessageCategory` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Status message category.

`MessageFullID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Status message full ID with severity.

`MessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier of the status message.

`MessageSeverity` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Severity of the status message.

| Value | Status message severity |
| --- | --- |
| 0x40000000 | Success |
| 0x80000000 | Warning |
| 0xC0000000 | Error |

`MessageState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

State of the message.

| Value | Message state |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | Error |

`NALPath` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The site's definition of the distribution point's location.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier for the package.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Source site for this status.

`StatusMsgID` Data type: `SInt64`

Access type: Read-only

Qualifiers: [not\_null, read]

Status message instance identifier. Link to `SMS_StatusMessage RecordID`.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).