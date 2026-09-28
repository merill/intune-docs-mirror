---
layout: Conceptual
title: SMS_SCI_MaintenanceTask Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_maintenancetask-server-wmi-class
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
description: Learn how to use the SMS_SCI_MaintenanceTask class to represent a site control item maintenance task.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c8331bab-d85c-4bf0-86ba-f0e6397a2641
document_version_independent_id: 32ee91fc-61fe-0e81-567d-8e4920512f90
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_maintenancetask-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_maintenancetask-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_maintenancetask-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: f7fd61a4-a36c-f09d-9157-f0e6c508e09f
---

# SMS_SCI_MaintenanceTask Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_MaintenanceTask` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a site control item maintenance task.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_MaintenanceTask : SMS_SiteControlItem
{
     String BackupLocation;
     DateTime BeginTime;
     UInt32 DaysOfWeek;
     Boolean Enabled;
     UInt32 FileType;
     String ItemName;
     String ItemType;
     DateTime LatestBeginTime;
     UInt32 NumRefreshDays;
     String SiteCode;
     String TaskName;
     UInt32 TaskType;
};
```

## Methods

The `SMS_SCI_MaintenanceTask` class does not define any methods.

## Properties

`BackupLocation` Data type: `String`

Access type: Read/Write

Qualifiers: None

The location of the backup for the maintenance task.

`BeginTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Beginning time for execution of the maintenance task. The default value is "00000000000000.000000+\*\*\*". Only the hours and minutes of this property are used.

`DaysOfWeek` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Days of the week on which the maintenance task executes. Possible values are listed below. The default value is SUNDAY (0).

| Value | Maintenance task day |
| --- | --- |
| 0 | SUNDAY |
| 1 | MONDAY |
| 2 | TUESDAY |
| 3 | WEDNESDAY |
| 4 | THURSDAY |
| 5 | FRIDAY |
| 6 | SATURDAY |

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the maintenance task is activated.

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`LatestBeginTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Latest beginning time of execution for the maintenance task. The default value is "00000000000000.000000+\*\*\*". Only the hours and minutes of this property are used.

`NumRefreshDays` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Number of days between maintenance task executions. The default value is 0.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`TaskName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the maintenance task.

`TaskType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Type of maintenance task. Currently the only possible value is BACKUP (1).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).