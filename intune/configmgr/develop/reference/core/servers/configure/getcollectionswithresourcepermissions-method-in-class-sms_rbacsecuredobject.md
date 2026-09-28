---
layout: Conceptual
title: GetCollectionsWithResourcePermissions Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject
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
description: In Configuration Manager, the GetCollectionsWithResourcePermissions WMI class method gets the list of collection identifiers for which the user has the specified permissions. The collection must contain the specified resource.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3cb8b0f6-5efe-0938-5c67-5688370b11fe
document_version_independent_id: 3a015538-f5ee-5ceb-ce7c-73f0ee8eb1f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e7cac873-4b8d-26f0-2823-0eab6c1f92d2
---

# GetCollectionsWithResourcePermissions Method - Configuration Manager | Microsoft Learn

The `GetCollectionsWithResourcePermissions` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the list of collection identifiers for which the user has the specified permissions. The collection must contain the specified resource.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 GetCollectionsWithResourcePermissions(
     UInt32 ResourceID,
     UInt32 Permissions,
     String CollectionIDs[]
);
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: [in]

Unique ID, supplied by Configuration Manager, for the resource.

`Permissions` Data type: `UInt32`

Qualifiers: [in]

Set of user permissions for the collections that contain the resource.

`CollectionIDs` Data type: `String` Array

Qualifiers: [out]

IDs of collections for which the user has the specified permissions.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).