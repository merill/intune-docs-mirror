---
layout: Conceptual
title: SMS_ClientSettingsAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsassignment-server-wmi-class
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
description: The SMS_ClientSettingsAssignment WMI class is an SMS Provider server class, in Configuration Manager, that represents the collection assignments of specified SMS_ClientSettings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 129ad93c-6b53-2fa7-fe2e-1b8b81a47da6
document_version_independent_id: e88fe8c8-adb9-f10b-e16a-31af978160a3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_clientsettingsassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_clientsettingsassignment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 19b7b442-eb21-4eda-4f6d-e7e4ac7bbc1d
---

# SMS_ClientSettingsAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_ClientSettingsAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the collection assignments of specified SMS\_ClientSettings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientSettingsAssignment : SMS_BaseClass
{
    UInt32 ClientSettingsID;
    String CollectionID;
    String CollectionName;
    DateTime CreationTime;
    String UniqueID;
};
```

## Methods

The `SMS_ClientSettingsAssignment` class does not define any methods.

## Properties

`ClientSettingsID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifies the client agent component. The Client Settings Agent ID is 1.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The ID for the collection associated with the client settings assignment.

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read]

The name of the collection associated with the client settings assignment.

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [notnull, read]

The date and time when the client settings assignment is created.

`UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [notnull, read]

The GUID of the client settings assignment.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).