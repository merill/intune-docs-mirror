---
layout: Conceptual
title: ImportRole Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/importrole-method-in-class-sms_role
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
description: The ImportRole Windows Management Instrumentation (WMI) class method imports a role defined by an XML string to the database.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6c007dbe-ddad-d6d5-577f-80d2880680db
document_version_independent_id: 0b24e555-b586-7e86-a7f6-7d3e6046c3d0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/importrole-method-in-class-sms_role.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/importrole-method-in-class-sms_role
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/importrole-method-in-class-sms_role.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5ee43b94-3bcd-3238-9db1-cf07bdf687c1
---

# ImportRole Method - Configuration Manager | Microsoft Learn

The `ImportRole` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports a role defined by an XML string to the database.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ImportRole(
     String RolesXml,
     Boolean OverwrittenExisted,
     String ErrorStr,
);
```

#### Parameters

`RolesXml` Data type: `String`

Qualifiers: [in]

The id of the role.

`OverwrittenExisted` Data type: `Boolean`

Qualifiers: [in]

`true`, if an existing role should be overwritten. The default value is true.

`ErrorStr` Data type: `String`

Qualifiers: [out]

The error information if there is any error while importing the role.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).