---
layout: Conceptual
title: UserHasPermissions Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject
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
description: In Configuration Manager, the UserHasPermissions Windows Management Instrumentation class method determines whether the current user has the requested permissions for the specified object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6848c55c-15dc-6a44-41c7-941d965807f2
document_version_independent_id: 4b07d30b-8268-1fff-0278-468480983c42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e503ead1-7a95-cb01-adca-0f8183e54292
---

# UserHasPermissions Method - Configuration Manager | Microsoft Learn

The `UserHasPermissions` Windows Management Instrumentation (WMI) class method, in Configuration Manager, determines whether the current user has the requested permissions for the specified object.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
Boolean UserHasPermissions(
     ref:SMS_BaseClass ObjectPath,
     UInt32 Permissions,
);
```

#### Parameters

`ObjectPath` Data type: `ref:SMS_BaseClass`

Qualifiers: [in]

Object being checked for access permissions, which can be a class name or instance path.

`Permissions` Data type: `UInt32`

Qualifiers: [in,out]

The permission the user has on the object specified by `ObjectPath`.

Possible values are defined by the properties of `SMS_SecuredObject Server WMI Class`.

## Return Values

Returns a `Boolean` data type that is `true` if the user has permissions.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).