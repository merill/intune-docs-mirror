---
layout: Conceptual
title: SMS_G_System_History Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_history-server-wmi-class
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
description: The SMS_G_System_History class is an SMS Provider server class that serves as an abstract base class representing hardware component state history for a client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1053cf57-5bf2-7e10-21d4-f2b58318c73a
document_version_independent_id: 567277a9-8429-d298-a387-77fc35e9966c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_history-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_history-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_history-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 50b74b22-6b36-f33e-e23a-d38fbc391d9c
---

# SMS_G_System_History Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_History` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as an abstract base class representing hardware component state history for a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_History : SMS_G_System
{
     UInt32 GroupID;
     UInt32 ResourceID;
     UInt32 RevisionID;
     DateTime TimeStamp;
};
```

## Methods

The `SMS_G_System_History` class does not define any methods.

## Properties

`GroupID` Data type: **UInt32**

Access type: Read-only

Qualifiers: [key]

ID of the group that distinguishes one hardware inventory instance from another within one client resource. For example, each logical disk object for a client is assigned a unique `GroupID` value.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

`RevisionID` Data type: **UInt32**

Access type: Read-only

Qualifiers: [key]

ID that increments if the object changes after the last time inventory was taken. The highest number indicates the most recent update. Objects with the same `ResourceID` and `GroupID` values are deltas. They differ from one another by the `RevisionID` number.

`TimeStamp` Data type: **DateTime**

Access type: Read-only

Qualifiers: None

Date and time of the inventory.

## Remarks

History objects are created from the current hardware component object when the component has changed since the last inventory. This class represents a collection of prior hardware component states for the client.

Your application uses this class to determine the state of client hardware at any given time. Names of derived history classes are prefixed with "SMS\_GEH\_System\_" followed by the inventoried object name. An example class name is `SMS_GEH_System_ACCOUNT`. Your application can use the derived classes to determine the state of a hardware component on a client at a given point in time.

Hardware history is deleted on a schedule if the Delete Aged Inventory History database maintenance task is set to `true` in the Configuration Manager console. You can also enable this task and set the schedule by updating the site control file. The site control item [SMS_SCI_SQLTask Server WMI Class](../../servers/configure/sms_sci_sqltask-server-wmi-class) object, and the `TaskName` value is "Delete Aged Inventory History". For an example that updates the site control file, see [About the site control file](../../../../core/understand/about-the-configuration-manager-site-control-file).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).