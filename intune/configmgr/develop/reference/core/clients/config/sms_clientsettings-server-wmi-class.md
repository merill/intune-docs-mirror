---
layout: Conceptual
title: SMS_ClientSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientsettings-server-wmi-class
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
description: Learn how to represent the settings that apply to the clients which belong to a specified collection using SMS_ClientSettings class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bcb4cdf6-f39a-d4f9-a0aa-75a4731ae39b
document_version_independent_id: 9da65657-f9d3-9211-5d4c-dd83992e82cc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_clientsettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_clientsettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_clientsettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9fca04c7-b3c3-358c-95f7-f2973f2a68d9
---

# SMS_ClientSettings Class - Configuration Manager | Microsoft Learn

The `SMS_ClientSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the settings that apply to the clients which belong to a specified collection. These settings override the default client settings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientSettings : SMS_ClientSettingsBase
{
    SMS_ClientAgentConfig_BaseClass AgentConfigurations[];
    UInt32 AssignmentCount;
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateModified;
    String Description;
    Boolean Enabled;
    UInt32 FeatureType;
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

The following table lists the methods in the `SMS_ClientSettings` class.

| Method | Description |
| --- | --- |
| [CheckPortalUrl Method for Class SMS_ClientSettings](checkportalurl-method-for-class-sms_clientsettings) | Checks whether the default application catalog website point in the default or custom client agent settings is set to `portalUrl`. |

## Properties

`AgentConfigurations` Data type: `SMS_ClientAgentConfig_BaseClass` Array

Access type: Read/Write

Qualifiers: none

`AgentConfigurations` is an array of type `SMS_ClientAgentConfig_BaseClass`. Many classes for individual features inherit from `SMS_ClientAgentConfig_BaseClass`. For example, `SMS_StateSystemConfig` and `SMS_HardwareInventoryAgentConfig`. You use these individual SMS\_\*Config classes to define the value of settings for their feature. The default value is null for `AgentConfigurations`.

`AssignmentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The count that how many collections are assigned to this setting. The default value is 0.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read, sizelimit]

Name of the user that created the client settings.

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

User defined description of the setting. The default value is &lt;null&gt;.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [notnull]

Reserved for future use.

`FeatureType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Indicates if the settings are applied to regular `SMS_ClientSettings` or `SMS_AntimalwareSettings`. The default value is 2 when you create `SMS_ClientSettings`. Possible values are:

| Value | Settings type |
| --- | --- |
| 1 | SMS\_AntimalwareSettings |
| 2 | SMS\_ClientSettings |

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Reserved for future use.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read, sizelimit]

Name of the user that last modified the client settings.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [notnull]

Name of the component.

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Priority is used by the client to decide which value to take if the client belongs to more than one collection and multiple collections have client settings defined. The higher the number, the lower the relative priority to the client. All settings should have different priority numbers. The default value is the next available priority number.

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

The name of the security scopes with which the setting is associated. The default value is "Default."

`SettingsID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

For internal use only.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Type indicates whether the settings are applied to Device or User. The default value is 1 (Device).

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