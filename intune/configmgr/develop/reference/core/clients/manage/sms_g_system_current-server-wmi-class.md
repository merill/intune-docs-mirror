---
layout: Conceptual
title: SMS_G_System_Current Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class
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
description: Learn how to represent the current client state at the time of the last hardware inventory using SMS_G_System_Current as an abstract base class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 91c9bbe7-ad65-e730-8da3-8b783bdb7bb7
document_version_independent_id: 3e3b4113-30c4-fa74-29e7-18d0fa8b633f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2e7d3e8e-9ac7-c8f4-20b1-297229464581
---

# SMS_G_System_Current Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_Current` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as an abstract base class and represents the current client state at the time of the last hardware inventory.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_Current : SMS_G_System
{
     UInt32 GroupID;
     UInt32 ResourceID;
     UInt32 RevisionID;
     DateTime TimeStamp;
};
```

## Methods

The `SMS_G_System_Current` class does not define any methods.

## Properties

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the group that distinguishes one hardware inventory instance from another within one client resource. For example, each logical disk instance for a client is assigned a unique `GroupID` value.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

For this class, the default value of this property is `null`.

`RevisionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID that increments if the object changes after the last time inventory was taken. The highest number indicates the most recent update. Objects with the same `ResourceID` and `GroupID` values are deltas. They differ from one another by the `RevisionID` number.

`TimeStamp` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time of the inventory.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Your application can query classes derived from `SMS_G_System_Current` to get the current state of individual client hardware components. Alternatively the application can query `SMS_G_System_Current` itself to get the current state of all client hardware components. For example, the following query retrieves all hardware components for the given client.

```
SELECT * FROM SMS_G_System_Current
WHERE ResourceID = <resourceid>
```

Although using this query is a simple solution for getting all the hardware components for a client, it is inefficient. WMI turns the query into multiple queries, one for each subclass, and creates a thread for each query. If performance is critical, your application should query each subclass specifically.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).