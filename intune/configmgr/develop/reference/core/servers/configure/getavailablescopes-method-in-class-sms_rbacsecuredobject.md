---
layout: Conceptual
title: GetAvailableScopes Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getavailablescopes-method-in-class-sms_rbacsecuredobject
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
description: The GetAvailableScopes Windows Management Instrumentation class method, in Configuration Manager, returns the secured scopes, which current user has the permission to grant to other accounts.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6f13d340-54b7-1c84-3485-c7b62f93b6c6
document_version_independent_id: 2b07938e-bee0-7d23-ae7b-976a36e0bd38
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getavailablescopes-method-in-class-sms_rbacsecuredobject.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getavailablescopes-method-in-class-sms_rbacsecuredobject
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getavailablescopes-method-in-class-sms_rbacsecuredobject.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3995f9c0-9850-0027-05a8-2bc33e1cb7ea
---

# GetAvailableScopes Method - Configuration Manager | Microsoft Learn

The `GetAvailableScopes` Windows Management Instrumentation (WMI) class method, in Configuration Manager, returns the secured scopes, which current user has the permission to grant to other accounts.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 GetAvailableScopes(
     String RoleIDs[],
     UInt32 ScopeTypeID,
     String ScopeIDs[],
     String ScopeNames[]
);
```

#### Parameters

`RoleIDs` Data type: `String` Array

Qualifiers: [in]

The role ID list which user uses to grant permissions to other accounts.

`ScopeTypeID` Data type: `UInt32`

Qualifiers: [in, optional]

Type of scope, could be RBA security category (29) or collection(1). The default value is 29.

| Value | Scope type |
| --- | --- |
| 1 | Collection |
| 29 | Secured scope. |

`ScopeIDs` Data type: `String` Array

Qualifiers: [out]

IDs of collections for which the user has the specified permissions.

`ScopeNames` Data type: `String` Array

Qualifiers: [out]

The name of the scopes.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).