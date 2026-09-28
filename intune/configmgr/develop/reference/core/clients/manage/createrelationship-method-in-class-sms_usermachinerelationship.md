---
layout: Conceptual
title: CreateRelationship method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/createrelationship-method-in-class-sms_usermachinerelationship
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
description: Use this WMI class method to add a user device affinity.
ms.date: 2020-08-26T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 93711dfe-93b5-e157-8477-e37a06159a56
document_version_independent_id: d0ae5dfe-1d77-74cc-91c6-d39c37a256b3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/createrelationship-method-in-class-sms_usermachinerelationship.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/createrelationship-method-in-class-sms_usermachinerelationship
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/createrelationship-method-in-class-sms_usermachinerelationship.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 3879f930-e1fb-5567-f708-8d8762bda5eb
---

# CreateRelationship method - Configuration Manager | Microsoft Learn

The `CreateRelationship` WMI class method creates a relationship between a user and a device.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 CreateRelationship (
     uint32 MachineResourceId,
     string UserAccountName,
     uint32 SourceId,
     uint32 TypeId
);
```

## Parameters

`MachineResourceId` Data type: `UInt32`

Qualifiers: `[in]`

Unique Configuration Manager-supplied identifier for the resource.

`UserAccountName` Data type: `String`

Qualifiers: `[in]`

User account name. For example, `contoso\jqpublic`.

`SourceId` Data type: `UInt32`

Qualifiers: `[in]`

Source object identifier for dependency.

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

`TypeId` Data type: `UInt32`

Qualifiers: `[in, optional]`

An array of types for this relationship. For a value of `1`, the **UniqueUserName** is the primary user. If the value is null, they aren't the primary user.

## Return values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).