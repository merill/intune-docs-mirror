---
layout: Conceptual
title: SMS_Permission Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_permission-server-wmi-class
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
description: The SMS_Permission Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents RBAC Security User Permissions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 09694a80-b93a-3f29-527b-b6d6cc552f84
document_version_independent_id: f1ecec5c-7676-210e-78db-ed59fcb17c80
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_permission-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_permission-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_permission-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9b475471-5797-e01b-bce9-49191e9e9dcf
---

# SMS_Permission Class - Configuration Manager | Microsoft Learn

The `SMS_Permission` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents RBAC Security User Permissions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Permission : SMS_BaseClass
{
    UInt32 AdminID;
    String CategoryID;
    String CategoryName;
    UInt32 CategoryTypeID;
    Boolean GrantedToCurrentUser;
    String LogonName;
    String RoleID;
    String RoleName;
};
```

## Methods

The `SMS_Permission` class doesn't define any methods.

## Properties

`AdminID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

ID of the admin account.

`CategoryID` Data type: `String`

Access type: Read

Qualifiers: [key]

ID of the RBA security category.

`CategoryName` Data type: `String`

Access type: Read

Qualifiers: None

Name of the RBA security category.

`CategoryTypeID` Data type: `UInt32`

Access type: Read

Qualifiers: [enumeration, key]

The type of the category. Possible values are listed below. The default value is 29.

| Value | Category type |
| --- | --- |
| 1 | Collection |
| 29 | SecuredScope |

`GrantedToCurrentUser` Data type: `Boolean`

Access type: Read

Qualifiers: None

This value will be true if this permission is granted to current user directly or indirectly (through a Security Group).

`LogonName` Data type: `String`

Access type: Read

Qualifiers: None

Sign-in name of the user.

`RoleID` Data type: `String`

Access type: Read

Qualifiers: [key]

ID of the role.

`RoleName` Data type: `String`

Access type: Read

Qualifiers: None

Name of the role.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).