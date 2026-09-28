---
layout: Conceptual
title: SMS_DistributionDPStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributiondpstatus-server-wmi-class
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
description: The SMS_DistributionDPStatus WMI class is an SMS Provider server class, in Configuration Manager, that represents a status message reported by a distribution point site system role.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cec2d675-f619-5ca6-4136-35e85e35f84e
document_version_independent_id: cd0a1df0-70e9-7346-26a5-763456a143b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_distributiondpstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_distributiondpstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_distributiondpstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f4d004c5-7da0-2476-013d-16ead3d5617c
---

# SMS_DistributionDPStatus Class - Configuration Manager | Microsoft Learn

The `SMS_DistributionDPStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a status message reported by a distribution point site system role.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionDPStatus : SMS_BaseClass
{
    UInt32 GroupCount;
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
    Boolean IsPeerDP;
    UInt64 LastStatusID;
    DateTime LastUpdateDate;
    UInt32 MessageCategory;
    UInt32 MessageFullID;
    UInt32 MessageID;
    UInt32 MessageSeverity;
    UInt32 MessageState;
    String NalPath;
    String Name;
    String ObjectID;
    UInt32 ObjectTypeID;
    String PackageID;
    String ResourceType;
    String SiteCode;
};
```

## Methods

The `SMS_DistributionDPStatus` class does not define any methods.

## Properties

`GroupCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of distribution point groups.

`ID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [key, read]

Distribution point ID. This value is stored in the database.

`InsString1` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 1.

`InsString10` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 10.

`InsString2` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 2.

`InsString3` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 3.

`InsString4` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 4.

`InsString5` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 5.

`InsString6` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 6.

`InsString7` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 7.

`InsString8` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 8.

`InsString9` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Inserted string 9.

`IsPeerDP` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this is a branch distribution point.

`LastStatusID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

Last status ID.

`LastUpdateDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date of the last status update.

`MessageCategory` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Status message category.

`MessageFullID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Status message full ID with severity.

`MessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Status message ID.

`MessageSeverity` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Status message severity.

| Value | Status message severity |
| --- | --- |
| 0x40000000 | Success |
| 0x80000000 | Warning |
| 0xC0000000 | Error |

`MessageState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Message state.

| Value | Message state |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | Error |

`NalPath` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Distribution point NALPath.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Distribution point name.

`ObjectID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

PackageID or ModelName.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Secured object class ID.

| Value | Object type |
| --- | --- |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Package ID deployed to this distribution point.

`ResourceType` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Resource type.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Source site for this status.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).