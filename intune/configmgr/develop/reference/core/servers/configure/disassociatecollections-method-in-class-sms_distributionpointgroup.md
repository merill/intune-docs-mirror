---
layout: Conceptual
title: DisassociateCollections Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/disassociatecollections-method-in-class-sms_distributionpointgroup
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
description: The DisassociateCollections Windows Management Instrumentation class method removes a set of associated collections from this distribution point group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fe2def8f-4d69-56d9-3af3-83a7733ae5e8
document_version_independent_id: 55c18ef6-6bd8-9c31-cc18-9d6dac67033e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/disassociatecollections-method-in-class-sms_distributionpointgroup.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/disassociatecollections-method-in-class-sms_distributionpointgroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/disassociatecollections-method-in-class-sms_distributionpointgroup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 40acc56f-9e89-f420-9b5e-a763916c7c80
---

# DisassociateCollections Method - Configuration Manager | Microsoft Learn

The `DisassociateCollections` Windows Management Instrumentation (WMI) class method, in Configuration Manager, removes a set of associated collections from this distribution point group.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 DisassociateCollections(
     string CollectionID[]
);
```

#### Parameters

`CollectionID` Data type: `String` Array

Qualifiers: `[in]`

The ID that refers to the collection.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).