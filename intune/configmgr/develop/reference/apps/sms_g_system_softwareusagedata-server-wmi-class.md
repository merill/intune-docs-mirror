---
layout: Conceptual
title: SMS_G_System_SoftwareUsageData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_system_softwareusagedata-server-wmi-class
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
description: Provides a view of raw metering data that combines file and user information with the raw data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 436e4fd1-202f-aac3-34f2-52957fb253de
document_version_independent_id: 0d521821-6595-fb43-2523-e78129459e57
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_g_system_softwareusagedata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_g_system_softwareusagedata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_g_system_softwareusagedata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: a4b138ac-fad0-ca62-8b9b-096b640b5a82
---

# SMS_G_System_SoftwareUsageData Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_SoftwareUsageData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides a view of raw metering data that combines file and user information with the raw data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_SoftwareUsageData : SMS_G_System
{
      String CompanyName;
      Boolean EndNotCaptured;
      DateTime EndTimeGMT;
      DateTime EndTimeLocal;
      String FileDescription;
      SInt64 FileID;
      String FileName;
      UInt32 FileSize;
      String FileVersion;
      Boolean InTSSession;
      String MeterDataID;
      UInt32 ProductLanguage;
      String ProductName;
      String ProductVersion;
      UInt32 ResourceID;
      Boolean StartNotCaptured;
      DateTime StartTimeGMT;
      DateTime StartTimeLocal;
      Boolean StillRunning;
      String UserName;
};
```

## Methods

The `SMS_G_System_SoftwareUsageData` class does not define any methods.

## Properties

`CompanyName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the company that made the file, taken from the `Company` property of the file version resources.

`EndNotCaptured` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the metering agent could not capture the actual end time of the process.

`EndTimeGMT` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [key]

The date and time, in Universal Coordinated Time (UTC), when the process stopped running, if `StillRunning` is `false`. If it is `true`, `EndTimeGMT` indicates the time when the data was reported.

`EndTimeLocal` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time, in the local time zone of the client, when the process stopped running, if `StillRunning` is `false`. If it is `true`, `EndTimeLocal` indicates the time when the data was reported.

`FileDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the metered file, taken from the files version resources.

`FileID` Data type: `SInt64`

Access type: Read/Write

Qualifiers: None

ID of the file that was metered. To find the file information, the application matches this property to the ID in [SMS_ProductFileInfo Server WMI Class](sms_productfileinfo-server-wmi-class). To find the rules that caused the file to be metered, the application matches `FileID` to the ID in [SMS_MeteredFiles Server WMI Class](sms_meteredfiles-server-wmi-class).

`FileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

File name of the metered file if the metering rule matched the file name. If it did not match, but the `OriginalFileName` property of the rule matched the original file name in the files version resources, this property represents the original file name.

`FileSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Size of the metered file.

`FileVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

File version of the metered file, taken from the file version resources.

`InTSSession` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file was used in a Terminal Server session. Set this property to `false` if the file was used in a console session.

`MeterDataID` Data type: `String`

Access type: Read/Write

Qualifiers:

[key]

Unique ID of a particular instance of a running process on a computer. A record with this ID is created every time the client reports on the same instance of a running program.

`ProductLanguage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Subtype("Locale Id")]

Language ID of the metered file, taken from the file version resources.

`ProductName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Product name of the metered file, taken from the file version resources. This is not the product name of the rule that caused the file to be metered.

`ProductVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Product version of the metered file, taken from the file version resources.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](../core/clients/manage/sms_g_system-server-wmi-class).

For this class, this property represents the ID of the computer that executed the metered program. To find the computer information, your application finds the record with the same resource ID in the [SMS_R_System Server WMI Class](../core/clients/manage/sms_r_system-server-wmi-class) class.

`StartNotCaptured` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the metering agent could not capture the actual start time of the process.

`StartTimeGMT` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time, in Universal Coordinated Time (UTC), when the program started.

`StartTimeLocal` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time, in the local time zone of the client, when the program started.

`StillRunning` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the program is still running. Set this property to `false` if `EndTime` represents the actual end time of the metered program.

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Fully qualified user name of the user of the metered application.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class counts the number of distinct users and computers that used a metered file during a particular interval on a particular site.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).