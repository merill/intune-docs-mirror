---
layout: Conceptual
title: GetClientsCountByCollections Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/getclientscountbycollections-method-in-class-sms_migrationcollectioninfo
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
description: A Windows Management Instrumentation class method that retrieves the number of clients in the specified collections.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 21438104-73a9-d6c2-ed2c-a1a30cc2ec7b
document_version_independent_id: de417369-bb20-f762-0880-6420bcff5b6c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/getclientscountbycollections-method-in-class-sms_migrationcollectioninfo.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/getclientscountbycollections-method-in-class-sms_migrationcollectioninfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/getclientscountbycollections-method-in-class-sms_migrationcollectioninfo.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 581ded5b-37b8-e652-7fc1-c6d0876e2c40
---

# GetClientsCountByCollections Method - Configuration Manager | Microsoft Learn

The `GetClientsCountByCollections` Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves the number of clients in the specified collections.

Note

This method is reserved for future use.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetClientsCountByCollections(
     String collectionIDs[],
     UInt32 clientsCount
);
```

#### Parameters

`collectionIDs` Data type: `String` array

Qualifiers: [in]

The specified collection IDs.

`clientsCount` Data type: `UInt32`

Qualifiers: `[out]`

The number of clients in the collections.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).