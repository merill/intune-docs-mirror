---
layout: Conceptual
title: GetEntityReferences Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/getentityreferences-method-in-class-sms_migrationentity
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
description: Learn how to get the referenced entities of the specified entities in Configuration Manager using GetEntityReferences class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8e447560-c693-ab40-19a1-91a64ff933bd
document_version_independent_id: 18551c29-7f68-9216-4e29-0a88ff980e04
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/getentityreferences-method-in-class-sms_migrationentity.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/getentityreferences-method-in-class-sms_migrationentity
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/getentityreferences-method-in-class-sms_migrationentity.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e08ba31-66bb-9882-7318-6213120191ed
---

# GetEntityReferences Method - Configuration Manager | Microsoft Learn

The `GetEntityReferences` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the referenced entities of the specified entities.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetEntityReferences(
     UInt32 entityIDs[],
     UInt32 referenceType,
     Boolean referenceDirection,
     UInt32 entityReferenceList[]
);
```

#### Parameters

`entityIDs` Data type: `UInt32` array

Qualifiers: [in]

List of entities input.

`referenceType` Data type: `UInt32`

Qualifiers: [in]

Reference type.

`referenceDirection` Data type: `Boolean` array

Qualifiers: [in]

A flag indicating whether this is querying referencing or being referenced.

`entityReferenceList` Data type: `UInt32` Array

Qualifiers: `[out]`

List of entities queried.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).