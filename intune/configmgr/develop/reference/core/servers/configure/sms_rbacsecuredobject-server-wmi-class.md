---
layout: Conceptual
title: SMS_RbacSecuredObject Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class
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
description: Learn how to use SMS_RbacSecuredObject class, in Configuration Manager, that represents the RBAC Security Object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 81829c62-52ac-5e63-de7f-43fd749e3a44
document_version_independent_id: a5290442-c9fa-ea32-2aba-bbdd3cdd1c48
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6cfc7dfc-6b2b-3964-9e2f-4d7a527aebe1
---

# SMS_RbacSecuredObject Class - Configuration Manager | Microsoft Learn

The `SMS_RbacSecuredObject` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the RBAC Security Object.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_RbacSecuredObject : SMS_BaseClass
{
    UInt32 AvailableInstanceOperations;
    UInt32 AvailableTypeOperations;
    UInt32 GrantedOperations;
    UInt32 ObjectTypeID;
    String ObjectTypeName;
    SMS_Operation Operations[];
};
```

## Methods

The following table lists the methods in the `SMS_RbacSecuredObject` class.

| Method | Description |
| --- | --- |
| [UserHasPermissions Method in Class SMS_RbacSecuredObject](userhaspermissions-method-in-class-sms_rbacsecuredobject) | Returns `true` if the current user has all the requested rights to the given object. |
| [GetCollectionsWithResourcePermissions Method in Class SMS_RbacSecuredObject](getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject) | Retrieves the collections that the given resource is a member of and the requested permissions. |
| [GetAvailableScopes Method in Class SMS_RbacSecuredObject](getavailablescopes-method-in-class-sms_rbacsecuredobject) | Returns the secured scopes which current user has all the specified roles associated. |
| [GetUserList Method in Class SMS_RbacSecuredObject](getuserlist-method-in-class-sms_rbacsecuredobject) | Returns the secured scopes which current user has all the specified roles associated. |

## Properties

`AvailableInstanceOperations` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Available instance level permissions. Detail at Operations.

`AvailableTypeOperations` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Available permissions. Detail at Operations.

`GrantedOperations` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The operations which are granted to the current user for this type of object.

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The type of object.

`ObjectTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("256")]

Name of the object type.

`Operations` Data type: `SMS_Operation` Array

Access type: Read/Write

Qualifiers: [lazy]

The list of operations which belong to this type.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).