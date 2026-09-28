---
layout: Conceptual
title: SMS_ClientSettingsBase Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsbase-server-wmi-class
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
description: The SMS_ClientSettingsBase WMI class is an SMS Provider server class, in Configuration Manager, that represents the base class used by several client settings related classes.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 117f3afc-f238-e228-1d17-a34dd54ac526
document_version_independent_id: f42bd240-da06-5d39-3959-d1aa4404f31c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsbase-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_clientsettingsbase-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsbase-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 76417e1c-6d9a-9178-46a5-97aa938c7368
---

# SMS_ClientSettingsBase Class - Configuration Manager | Microsoft Learn

The `SMS_ClientSettingsBase` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the base class used by several client settings related classes (`SMS_AntimalwareSettings`, `SMS_ClientSettings`, and so on) for their simple properties.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientSettingsBase : SMS_BaseClass
{
    UInt32 AssignmentCount;
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateModified;
    String Description;
    Boolean Enabled;
    UInt32 Flags;
    String LastModifiedBy;
    String Name;
    UInt32 Priority;
    String SecuredScopeNames[];
    UInt32 SettingsID;
    UInt32 Type;
    String UniqueID;
};
```

## Methods

The `SMS_ClientSettingsBase` class doesn't define any methods.

## Properties

`AssignmentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Indicates how many collections are assigned to this client setting. The default value is 0.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read, sizelimit("512")]

Name of the user who created the client settings.

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [notnull, read]

The date and time when the client settings are created.

`DateModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [notnull, read]

The date and time when the client settings are modified.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [notnull]

An administrator generated description describing the settings configuration.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [notnull]

`true` if the agent is enabled.

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Reserved for future use.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read, sizelimit("512")]

Name of the user who last modified the client settings.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [notnull]

The name of the component.

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Priority is used by the client to decide which value to take if the client belongs to more than one collection and multiple collections have client settings defined. The higher the number, the lower the relative priority to the client. All settings should have different priority numbers. The default value is the next available priority number.

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

The name of the security scopes with which the setting is associated. The default value is "Default".

`SettingsID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

For internal use only.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Type indicates whether the settings is applied to Device or User. The default value is 1 (Device).

| Value | Settings type |
| --- | --- |
| 1 | Device |
| 2 | User |

`UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read, sizelimit("64")]

For internal use only.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).