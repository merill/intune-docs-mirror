---
layout: Conceptual
title: SMS_G_SYSTEM_ResourceClientSettingsAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_resourceclientsettingsassignment-server-wmi-class
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
description: Learn how to represent resource-specific client agent settings assignments in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e73e4a13-44ab-dc41-4516-709b0112fb24
document_version_independent_id: 159de651-68d1-cdb6-84b2-b17307b21d01
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_resourceclientsettingsassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_resourceclientsettingsassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_resourceclientsettingsassignment-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: afcef1b2-42fd-06fa-56b4-e0d4e3dd1460
---

# SMS_G_SYSTEM_ResourceClientSettingsAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_ResourceClientSettingsAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents resource-specific (device or user) client agent settings assignments.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_ResourceClientSettingsAssignment : SMS_G_System
{
     String AssignmentUniqueID;
     String CollectionName;
     UInt32 ID;
     String Name;
     UInt32 Priority;
     String UniqueID;
     UInt32 ResourceID;
     UInt32 Type;
};
```

## Methods

The `SMS_G_System_ResourceClientSettingsAssignment` class does not define any methods.

## Properties

`AssignmentUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Assignment Unique ID.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the collection.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Identifier.

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Identifier.

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: None

Unique identifier for the settings.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Settings type. Possible values are:

| Value | Settings type |
| --- | --- |
| 1 | Device |
| 2 | User |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).