---
layout: Conceptual
title: SMS_MeterData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_meterdata-server-wmi-class
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
description: The SMS_MeterData Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents captured software metering data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7d08f031-fb2d-5369-b607-9f83fb9ca90a
document_version_independent_id: 00f1da10-fe96-77c0-b4ca-2d6daff73cb5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_meterdata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_meterdata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_meterdata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 10f0686e-6b95-faf4-3238-9c8ed1891a6f
---

# SMS_MeterData Class - Configuration Manager | Microsoft Learn

The `SMS_MeterData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents captured software metering data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MeterData : SMS_BaseClass
{
      Boolean EndNotCaptured;
      DateTime EndTime;
      UInt32 EndTimeOffset;
      SInt64 FileID;
      Boolean InTSSession;
      String MeterDataID;
      UInt32 MeteredUserID;
      Boolean Released;
      UInt32 ResourceID;
      Boolean Started;
      Boolean StartNotCaptured;
      DateTime StartTime;
      UInt32 StartTimeOffset;
      Boolean StillRunning;
      UInt32 TimeSerial;
};
```

## Methods

The `SMS_MeterData` class does not define any methods.

## Properties

`EndNotCaptured` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the metering agent could not capture the actual end time of the process.

`EndTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [key]

The date and time, in Universal Coordinated Time (UTC), when the process stopped running, if `StillRunning` is `false`. If it is `true`, `EndTime` represents the time at which the data was reported.

`EndTimeOffset` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The offset from UTC, in minutes, of the local time for the client at the time the data was reported.

`FileID` Data type: `SInt64`

Access type: Read/Write

Qualifiers: None

ID of the file that was metered. To find the file information, match `FileID` with the ID in [SMS_ProductFileInfo Server WMI Class](sms_productfileinfo-server-wmi-class). To find the rules that caused the file to be metered, match `FileID` with the ID in [SMS_MeteredFiles Server WMI Class](sms_meteredfiles-server-wmi-class).

`InTSSession` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file was used in a Terminal Server session. Set the property to `false` if the file was used in a console session.

`MeterDataID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of a particular instance of a running process on a particular computer. A record with this ID is created every time the client reports on the same instance of a running program.

`MeteredUserID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the Windows user account of the programs user. To find the user name, the application finds the record with the same `MeteredUserID` property in the [SMS_MeteredUser Server WMI Class](sms_metereduser-server-wmi-class) class.

`Released` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Internal flag used by the metering system and signifying that the record can be deleted by the Delete Aged Software Metering Data site maintenance task.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the computer that executed the metered program. To find the computer information, your application finds the record with the same resource ID in the [SMS_R_System Server WMI Class](../core/clients/manage/sms_r_system-server-wmi-class) class.

`Started` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if this is the first record reporting on a particular instance of a running program. If this property is set to `true`, `StartTime` represents the actual time when the program started.

`StartNotCaptured` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the metering agent was not able to capture the actual start time of the process.

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time, in Universal Coordinated Time (UTC), when the program started, if `Started` is `true`. If it is `false`, `StartTime` is the end time (`EndTime`) of the previous report for this program.

`StartTimeOffset` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The offset from UTC, in minutes, of the local time for the client at the time the data was reported.

`StillRunning` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the program is still running. Set this property to `false` if `EndTime` represents the actual end time of the metered program.

`TimeSerial` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

A rough ordering of the time used to process the record. Records with a smaller `TimeSerial` value were processed before a record with a larger `TimeSerial` value. This property is not unique across records.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Each record represents a report of a running program on a computer. If a program runs over several reporting cycles, there are several instances of `SMS_MeterData` that report on it, all with the same `MeterDataID` value. The time periods specified by `StartTime` and `EndTime` are consecutive and do not overlap. The full period of program execution can be found by the earliest `StartTime` value (where `Started` = 1) and the latest `EndTime` value (where `StillRunning` = 0).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).