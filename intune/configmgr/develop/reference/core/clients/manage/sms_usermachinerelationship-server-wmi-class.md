---
layout: Conceptual
title: SMS_UserMachineRelationship class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_usermachinerelationship-server-wmi-class
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
description: Use this server WMI class to manage user device affinity.
ms.date: 2020-08-26T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 768c3af0-295b-772d-11fd-4de326a200e0
document_version_independent_id: a279c605-9a16-c2d0-ea2b-bd5b9fb21bf5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_usermachinerelationship-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_usermachinerelationship-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_usermachinerelationship-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 0c7744da-ca61-8d2e-ba82-a92ec58e77fe
---

# SMS_UserMachineRelationship class - Configuration Manager | Microsoft Learn

The `SMS_UserMachineRelationship` WMI class contains relationships between a device and its primary users.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UserMachineRelationship : SMS_BaseClass
{
    DateTime CreationTime;
    Boolean IsActive;
    UInt32 RelationshipResourceID;
    UInt32 ResourceClientType;
    UInt32 ResourceID;
    String ResourceName;
    UInt32 Sources[];
    UInt32 Types[];
    String UniqueUserName;
};
```

## Methods

The `SMS_UserMachineRelationship` class defines the following methods.

| Method | Description |
| --- | --- |
| [AddSource Method in Class SMS_UserMachineRelationship](addsource-method-in-class-sms_usermachinerelationship) | Adds a source for the relationship between the user and the device. |
| [AddType Method in Class SMS_UserMachineRelationship](addtype-method-in-class-sms_usermachinerelationship) | Adds a type of the relationship between a user and a device. |
| [CreateRelationship Method in Class SMS_UserMachineRelationship](createrelationship-method-in-class-sms_usermachinerelationship) | Creates a relationship between a user and a device. |
| [RemoveSource Method in Class SMS_UserMachineRelationship](removesource-method-in-class-sms_usermachinerelationship) | Removes a source for the relationship between a user and a device. |
| [RemoveType Method in Class SMS_UserMachineRelationship](removetype-method-in-class-sms_usermachinerelationship) | Removes a type of the relationship between a user and a device. |

## Properties

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time that the relationship was created.

`IsActive` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

**TRUE** if the relationship is active.

`RelationshipResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The unique identifier for this relationship.

`ResourceClientType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Client type for computer.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

The resource ID of the device.

`ResourceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The resource name of the device.

`Sources` Data type: `UInt32` Array

Access type: Read-only

Qualifiers: [read]

An array of sources for this relationship, with one of the following values:

| Value | Name | Description |
| --- | --- | --- |
| `1` | Self-service portal | The end user enabled the relationship by selecting the option in Software Center. |
| `2` | Administrator | An administrator created the relationship manually in the console. |
| `3` | User | Unused/deprecated. |
| `4` | Usage agent | The threshold of activity triggered a relationship to be created. |
| `5` | Device management | The user and device were tied together during on-prem MDM enrollment. |
| `6` | OSD | The user and device were tied together as part of an OS deployment task sequence. |
| `7` | Fast install | The user/device were tied together temporarily to enable an on-demand install from the catalog if no UDA relationship installed before the Install was triggered. |
| `8` | Exchange Server connector | The device was provisioned through Exchange ActiveSync. |
| `9` | Secure usage agent |  |

`Types` Data type: `UInt32` Array

Access type: Read-only

Qualifiers: [read]

An array of types for this relationship. For a value of `1`, the **UniqueUserName** is the primary user. If the value is null, they aren't the primary user.

`UniqueUserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

User name in domain\user format.

## Remarks

## Requirements

### Runtime requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).