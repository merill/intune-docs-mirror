---
layout: Conceptual
title: SMS_StatMsgWithInsStrings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgwithinsstrings-server-wmi-class
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
description: Learn how to use the SMS_StatMsgWithInsStrings class in Configuration Manager to set an individual status message with insertion strings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a19f1139-8331-06fd-ba18-eb31cf07110e
document_version_independent_id: f169159d-108a-6285-11c0-32e475ff5eb7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgwithinsstrings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_statmsgwithinsstrings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_statmsgwithinsstrings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 45956583-356a-9424-1f19-1068789e2270
---

# SMS_StatMsgWithInsStrings Class - Configuration Manager | Microsoft Learn

The `SMS_StatMsgWithInsStrings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an individual status message with insertion strings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StatMsgWithInsStrings : SMS_BaseClass
{
    String Component;
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
    String MachineName;
    UInt32 MessageID;
    UInt32 MessageType;
    String ModuleName;
    UInt32 PerClient;
    UInt32 ProcessID;
    SInt64 RecordID;
    UInt32 ReportFunction;
    UInt32 ResourceID;
    UInt32 Severity;
    String SiteCode;
    UInt32 SuccessfulTransaction;
    UInt32 ThreadID;
    DateTime Time;
    String TopLevelSiteCode;
    UInt32 Transaction;
    UInt32 Win32Error;
};
```

## Methods

The `SMS_StatMsgWithInsStrings` class does not define any methods.

## Properties

`Component` Data type: `String`

Access type: Read

Qualifiers: None

Name of the component that created the message. For user-defined messages, this name comes from the ApplicationName context qualifier that you must set before calling a raise status message method.

`InsString1` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 1.

`InsString10` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 10.

`InsString2` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 2.

`InsString3` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 3.

`InsString4` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 4.

`InsString5` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 5.

`InsString6` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 6.

`InsString7` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 7.

`InsString8` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 8.

`InsString9` Data type: `String`

Access type: Read

Qualifiers: None

Insertion string at position 9.

`MachineName` Data type: `String`

Access type: Read

Qualifiers: None

Name of the computer that created the message. For user-defined messages, this name comes from the MachineName context qualifier that you must set before calling a raise status message method.

`MessageID` Data type: `UInt32`

Access type: Read

Qualifiers: None

Unique ID of message text in a message DLL. See the MessageID property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`MessageType` Data type: `UInt32`

Access type: Read

Qualifiers: None

Type of message. See the MessageType property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`ModuleName` Data type: `String`

Access type: Read

Qualifiers: None

The DLL that is associated with the status message to raise. This is not the name of the DLL itself, but it is a display string corresponding to the ModuleName property value defined in [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class). You use the ModuleName value to get the DLL name.

`PerClient` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating if the status message was generated by a client component. See the PerClient property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`ProcessID` Data type: `UInt32`

Access type: Read

Qualifiers: None

ID of the process that created the message.

`RecordID` Data type: `SInt64`

Access type: Read

Qualifiers: [key]

Unique ID of the status message.

`ReportFunction` Data type: `UInt32`

Access type: Read

Qualifiers: None

Report function. See the ReportFunction property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`ResourceID` Data type: `UInt32`

Access type: Read

Qualifiers: None

Resource ID of the client, may be NULL if the message is not associated with a client.

`Severity` Data type: `UInt32`

Access type: Read

Qualifiers: None

Type of status message. See the Severity property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: None

Site code of the site that reported the status message.

`SuccessfulTransaction` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating transaction status. See the SuccessfulTransaction property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`ThreadID` Data type: `UInt32`

Access type: Read

Qualifiers: None

Identifier of the thread that created the message.

`Time` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time, in Universal Coordinated Time (UTC), when the status message was created.

`TopLevelSiteCode` Data type: `String`

Access type: Read

Qualifiers: None

This property is deprecated.

`Transaction` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating whether transactions are enabled. See the Transaction property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`Win32Error` Data type: `UInt32`

Access type: Read

Qualifiers: None

Win32 error code that is associated with the status message.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).