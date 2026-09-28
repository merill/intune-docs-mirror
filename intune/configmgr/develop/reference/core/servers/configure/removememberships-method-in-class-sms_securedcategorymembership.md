---
layout: Conceptual
title: RemoveMemberships Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removememberships-method-in-class-sms_securedcategorymembership
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
description: The RemoveMemberships Windows Management Instrumentation (WMI) class method is a batch operation to remove objects from categories.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 61cd2781-aabc-b217-9664-6ce0eaef3e52
document_version_independent_id: 96e75101-8461-1a8b-52b9-c95503ee88b9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/removememberships-method-in-class-sms_securedcategorymembership.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/removememberships-method-in-class-sms_securedcategorymembership
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/removememberships-method-in-class-sms_securedcategorymembership.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 03741bcb-849b-50a0-67bd-4f7927dc8c71
---

# RemoveMemberships Method - Configuration Manager | Microsoft Learn

The `RemoveMemberships` Windows Management Instrumentation (WMI) class method, in Configuration Manager, is a batch operation to remove objects from categories.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RemoveMemberships(
    String   ObjectIDs[],
    Uint32   ObjectTypeIDs[],
    String   CategoryIDs[]
);
```

#### Parameters

`ObjectIDs` Data type: `String` Array

Qualifiers: [in]

The array of object IDs.

`ObjectTypeIDs` Data type: `UInt32` Array

Qualifiers: [in]

The array of corresponding object type ID.

`CategoryIDs` Data type: `String` Array

Qualifiers: [in]

The array of corresponding security category IDs which those objects will be removed from.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).