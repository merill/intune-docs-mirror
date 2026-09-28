---
layout: Conceptual
title: SMS_ConfigurationItemSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemsettings-server-wmi-class
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
description: Learn how to represent configuration item settings using the SMS_ConfigurationItemSettings class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7cc39226-c505-67b2-6967-79f104166871
document_version_independent_id: fa05366d-1c57-a6c4-6cdc-dca9472385d6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_configurationitemsettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_configurationitemsettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_configurationitemsettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 54384d88-67fd-f574-63ad-bb104b280d96
---

# SMS_ConfigurationItemSettings Class - Configuration Manager | Microsoft Learn

The `SMS_ConfigurationItemSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents configuration item settings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationItemSettings : SMS_BaseClass
{
    UInt32 CI_ID;
    String CI_UniqueID;
    UInt32 DataType;
    String ModelName;
    UInt32 Setting_ID;
    String Setting_UniqueID;
    String SettingDescription;
    String SettingName;
    UInt32 SourceType;
};
```

## Methods

The `SMS_ConfigurationItemSettings` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`DataType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Defines the type of setting (integer, string, and so on) to facilitate rule authoring and evaluation.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`Setting_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The database identifier of a setting in the configuration item.

`Setting_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Uniquely identifies a setting defined in the configuration item.

`SettingDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the setting.

`SettingName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the setting.

`SourceType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The setting discovery provider type defined, if this setting is discovered from the registry, file system, WMI and so on.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).