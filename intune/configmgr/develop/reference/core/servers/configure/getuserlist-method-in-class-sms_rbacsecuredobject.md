---
layout: Conceptual
title: GetUserList Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getuserlist-method-in-class-sms_rbacsecuredobject
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
description: Learn how to get the list of users who have been granted permission to this object with the GetUserList method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 76bec6b4-7219-434c-4d1b-96dc834a7915
document_version_independent_id: 20ff4820-cf16-cdff-844c-56287a4816f6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getuserlist-method-in-class-sms_rbacsecuredobject.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getuserlist-method-in-class-sms_rbacsecuredobject
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getuserlist-method-in-class-sms_rbacsecuredobject.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6481250-83de-095f-e7aa-5f499efc2426
---

# GetUserList Method - Configuration Manager | Microsoft Learn

The `GetUserList` Windows Management Instrumentation (WMI) class method, in Configuration Manager, returns the list of users who have been granted permission to this object.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 GetUserList(
     SMS_BaseClass ref ObjectPath,
     String UserNames[],
     Uint32 PermittedOperations[]
);
```

#### Parameters

`ObjectPath` Data type: `SMS_BaseClass`

Qualifiers: [in]

The path of the object.

`UserNames` Data type: `String` Array

Qualifiers: [out]

Logon names of the users.

`PermittedOperations` Data type: `UInt32` Array

Qualifiers: [out]

Granted permissions.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).