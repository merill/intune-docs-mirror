---
layout: Conceptual
title: SMS_ClientSettingsDefault Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsdefault-server-wmi-class
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
description: An SMS Provider server class that represents simple read-only default client settings properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 58e90627-58f5-a149-b00f-45e657c62078
document_version_independent_id: 85dcebac-6a70-e893-5251-e6835399675c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsdefault-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_clientsettingsdefault-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsdefault-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8066ca6a-c061-75d6-12dd-b6f197d18c82
---

# SMS_ClientSettingsDefault Class - Configuration Manager | Microsoft Learn

The `SMS_ClientSettingsDefault` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents simple read-only default client settings properties.

Note

Nothing in this class should be modified.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientSettingsDefault : SMS_BaseClass
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
    UInt32 SettingsID;
    String SiteCode;
    UInt32 Type;
    String UniqueID;
};
```

## Methods

The `SMS_ClientSettingsDefault` class doesn't define any methods.

## Properties

`AssignmentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

`AssignmentCount` is 0 only. In general, the default client settings apply to all clients in the hierarchy, unless overridden by values defined in `SMS_ClientSettings`, which applies to certain collections.

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

Description is specified internally.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [notnull]

Reserved for future use.

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

Compared to `SMS_ClientSettings`, the priority is the lowest for `SMS_ClientSettingsDefault` (highest number) and shouldn't be changed.

`SettingsID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

For internal use only.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read]

Three-letter site code for the CAS site.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [notnull]

Type is used to indicate if this setting is 'Device,' 'User,' or 'Default.' For `SMS_ClientSettingsDefault`, it's 0 meaning 'Default.'

| Value | Setting type |
| --- | --- |
| 0 | Default |
| 1 | Device |
| 2 | User |

`UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read, sizelimit("64")]

The unique ID of the object.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).