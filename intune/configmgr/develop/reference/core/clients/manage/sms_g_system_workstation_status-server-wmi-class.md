---
layout: Conceptual
title: SMS_G_System_WORKSTATION_STATUS Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_workstation_status-server-wmi-class
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
description: In the Configuration Manager, the SMS_G_System_WORKSTATION_STATUS Windows Management Instrumentation class is an SMS Provider server class that contains information about the last time inventory was collected on a client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 69d58622-5688-2cdf-629d-0ab47d00dd28
document_version_independent_id: e855f500-6dcc-71a5-ca11-3a4dceac8d61
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_workstation_status-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_workstation_status-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_workstation_status-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bb4bef60-3a0b-a987-55d7-5e9189f9640c
---

# SMS_G_System_WORKSTATION_STATUS Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_WORKSTATION_STATUS` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains information about the last time inventory was collected on a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_WORKSTATION_STATUS : SMS_G_System_Current
{
     UInt32 GroupID;
     DateTime LastHardwareScan;
     String LastReportVersion;
     UInt32 ResourceID;
     UInt32 RevisionID;
     UInt32 SystemDefaultLocaleID;
     DateTime TimeStamp;
     UInt32 TimeZoneOffset
};
```

## Methods

The `SMS_G_System_WORKSTATION_STATUS` class does not define any methods.

## Properties

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is NULL.

`LastHardwareScan` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when Configuration Manager inventoried the client computer hardware.

`LastReportVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version of the last report.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`RevisionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`SystemDefaultLocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

System default locale ID.

`TimeStamp` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`TimeZoneOffset` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

System default time zone offset.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).