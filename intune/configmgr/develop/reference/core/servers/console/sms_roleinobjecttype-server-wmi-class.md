---
layout: Conceptual
title: SMS_RoleInObjectType Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_roleinobjecttype-server-wmi-class
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
description: Learn how to map a role and its associated object types in Configuration Manager using the SMS_RoleInObjectType class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 99999763-4c17-b4bc-c598-310a662f4720
document_version_independent_id: 0ed858da-1b99-9131-124d-f69906f187d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/console/sms_roleinobjecttype-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/console/sms_roleinobjecttype-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/console/sms_roleinobjecttype-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 74d635eb-8891-c93b-5140-8e014c75608d
---

# SMS_RoleInObjectType Class - Configuration Manager | Microsoft Learn

The `SMS_RoleInObjectType` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that maps a role and its associated object types.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_RoleInObjectType : SMS_BaseClass
{
    UInt32 ObjectTypeID;
    String RoleID;
};
```

## Methods

The `SMS_RoleInObjectType` class doesn't define any methods.

## Properties

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Secured object class ID. Possible values are listed below.

| Value | Object type ID |
| --- | --- |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 21 | SMS\_DeviceSettingPackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`RoleID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The ID of the role.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).