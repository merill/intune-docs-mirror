---
layout: Conceptual
title: SMS_DPGroupDistributionStatusDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatusdetails-server-wmi-class
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
description: The SMS_DPGroupDistributionStatusDetails WMI class is an SMS Provider server class, in Configuration Manager, that represents distribution point status details.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ec58ca8b-f1d2-a91d-e161-cd91b3634dcd
document_version_independent_id: 1a2a1ba2-7ff4-9e98-ab30-85190b3f08a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatusdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatusdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatusdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d1e3bf4b-4b3f-d831-1027-aca9b6643697
---

# SMS_DPGroupDistributionStatusDetails Class - Configuration Manager | Microsoft Learn

The `SMS_DPGroupDistributionStatusDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents distribution point status details.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupDistributionStatusDetails : SMS_BaseClass
{
    String ContentName;
    String DPName;
    String GroupID;
    UInt64 ID;
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
    UInt32 MessageCategory;
    UInt32 MessageFullID;
    UInt32 MessageID;
    UInt32 MessageSeverity;
    UInt32 MessageState;
    String ObjectID;
    UInt32 ObjectType;
    UInt32 ObjectTypeID;
    String PackageID;
    String SiteCode;
    UInt64 StatusMsgID;
    DateTime StatusTime;
};
```

## Methods

The `SMS_DPGroupDistributionStatusDetails` class does not define any methods.

## Properties

`ContentName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the package or application.

`DPName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the distribution point.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for the distribution point group.

`ID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

Status message identifier.

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

`MessageCategory` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Status message category.

`MessageFullID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Status message full ID with severity.

`MessageID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier for the status message.

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

Qualifiers: [enumeration, read]

State of the message.

| Value | Message state |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | Error |

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the package or application.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Object type.

| Value | Object type |
| --- | --- |
| Value | Description |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | APPLICATION |

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Secured object class ID.

| Value | Object type |
| --- | --- |
| Value | Description |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifier for the package.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Source site for this status.

`StatusMsgID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

Status message instance identifier.

`StatusTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_StatusMessage Server WMI Class](../manage/sms_statusmessage-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).