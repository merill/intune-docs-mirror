---
layout: Conceptual
title: AddMemberships Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addmemberships-method-in-class-sms_securedcategorymembership
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
description: Learn how to use the AddMemberships Windows Management Instrumentation (WMI) class method, in Configuration Manager, for a batch operation to assign objects to security categories.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2f45d909-cc61-ad4d-4a88-9be117021eb8
document_version_independent_id: d05fb80c-db2a-4777-e097-2e6fb21cad74
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/addmemberships-method-in-class-sms_securedcategorymembership.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/addmemberships-method-in-class-sms_securedcategorymembership
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/addmemberships-method-in-class-sms_securedcategorymembership.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 0c73a5cc-ae0c-22c3-45d5-fbafc8b28999
---

# AddMemberships Method - Configuration Manager | Microsoft Learn

The `AddMemberships` Windows Management Instrumentation (WMI) class method, in Configuration Manager, is a batch operation to assign objects to security categories.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddMemberships(
     String ObjectIDs[],
     UInt32 ObjectTypeIDs[],
     String CategoryIDs[],
);
```

#### Parameters

`ObjectIDs` Data type: `String` Array

Qualifiers: [in]

Array of object IDs.

`ObjectTypeIDs` Data type: `UInt32` Array

Qualifiers: [in]

Array of object type IDs.

`CategoryIDs` Data type: `String` Array

Qualifiers: [in]

The security category IDs that the objects will be assigned to.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).