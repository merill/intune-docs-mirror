---
layout: Conceptual
title: SMS_ServiceWindow Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class
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
description: Learn how to use the SMS_ServiceWindow class to represent a window of time called a maintenance window, in which a program is allowed to execute on a group of computers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9ea289d6-ebd4-45c0-ea25-5e360c2adacb
document_version_independent_id: b699686a-182f-4348-ec04-c5f573e714fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 967a2b68-f2d9-b08e-a5e1-7443c4904f0a
---

# SMS_ServiceWindow Class - Configuration Manager | Microsoft Learn

The `SMS_ServiceWindow` Windows Management Instrumentation (WMI) class, in Configuration Manager, is an SMS Provider server class that represents a window of time, called a maintenance window, in which a program is allowed to execute on a group of computers.

## Syntax

```
Class SMS_ServiceWindow
{
      String Description
      UInt32 Duration
      Boolean IsEnabled
      Boolean IsGMT
      String Name
      UInt32 RecurrenceType
      String ServiceWindowID
      String ServiceWindowSchedules
      UInt32 ServiceWindowType
      DateTime StartTime
}
```

## Methods

The `SMS_ServiceWindow` class doesn't define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

The maintenance window description. The default value is "".

`Duration` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The duration, in minutes, of the maintenance window. The default value is 5.

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the maintenance window is enabled. The default value is `false`.

`IsGMT` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the start time is in Universal Coordinated Time (UTC). The default value is `false`.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

The maintenance window name. The default value is "".

`RecurrenceType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, enumeration]

The schedule recurrence. Possible values are listed below. The default value is NONE (1).

| Value | Recurrence type |
| --- | --- |
| 1 | NONE |
| 2 | DAILY |
| 3 | WEEKLY |
| 4 | MONTHLYBYWEEKDAY |
| 5 | MONTHLYBYDATE |

`ServiceWindowID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

A unique ID for the maintenance window. The default value is "".

`ServiceWindowSchedules` Data type: `String`

Access type: Read/Write

Qualifiers: None

The maintenance window schedules in schedule token format. Some valid recurring maintenance window schedules are:

0034394008100008 -- every 1 day(s), 1:00:00 AM

00343940081A2000 -- every 1 week(s), 1:00:00 AM

0034394008284400 -- every 1 month(s), 1:00:00 AM

The default value is "".

Note

Creating a schedule token is described in How to Create a Schedule Token.

`ServiceWindowType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The maintenance window type. Possible values are listed below. The default value is GENERAL (1).

| Value | Maintenance window type |
| --- | --- |
| 1 | GENERAL. General maintenance window. |
| 4 | UPDATES. Software Updates maintenance window. |
| 5 | OSD. Operating system deployment task sequence maintenance window. |

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The date and time indicating the start time for the maintenance window.

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    The maintenance window represented by this class has start and end times that can span days. The time span allows you to select certain hours of the week during which the client can execute the targeted programs and software updates. You can define maintenance windows for all Data Center computers by modifying the `Service Window` property of the Data Center collection.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).