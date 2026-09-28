---
layout: Conceptual
title: SMS_APermission Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_apermission-server-wmi-class
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
description: Learn how to describe the permission granted to a specific admin in Configuration Manager using SMS_APermission class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: df3d25d1-024c-b905-a38b-b71e311ffa18
document_version_independent_id: a2106fa7-6acb-e746-0a9a-89cc4f6e34ae
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_apermission-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_apermission-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_apermission-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 62c3bb6c-f78b-864e-7e0a-37d247f31c0a
---

# SMS_APermission Class - Configuration Manager | Microsoft Learn

The `SMS_APermission` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is embedded by `SMS_Admin` and describes the permission granted to a specific admin.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_APermission :
{
    String CategoryID;
    String CategoryName;
    UInt32 CategoryTypeID;
    String RoleID;
    String RoleName;
};
```

## Methods

The `SMS_APermission` class does not define any methods.

## Properties

`CategoryID` Data type: `String`

Access type: Read/Write

Qualifiers: None

ID of the associated RBA security category or collection.

`CategoryName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the RBA security category or collection.

`CategoryTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The type of category. The default value is 29.

| Value | Category type |
| --- | --- |
| 1 | Collection |
| 29 | SecuredScope |

`RoleID` Data type: `String`

Access type: Read/Write

Qualifiers: None

ID of the security role.

`RoleName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the role.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).