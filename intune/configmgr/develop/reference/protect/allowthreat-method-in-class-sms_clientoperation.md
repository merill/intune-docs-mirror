---
layout: Conceptual
title: AllowThreat Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/allowthreat-method-in-class-sms_clientoperation
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
description: In Configuration Manager, the AllowThreat WMI class method that allows the specified threat to all members in a specific collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9ca877de-827c-4149-6803-ffa6af92a9df
document_version_independent_id: 70c4e2cc-d9f2-1799-3047-1e6c43a4d4ed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/allowthreat-method-in-class-sms_clientoperation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/allowthreat-method-in-class-sms_clientoperation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/allowthreat-method-in-class-sms_clientoperation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 26e9d424-6c1b-0bde-aaa8-c3816d90a22e
---

# AllowThreat Method - Configuration Manager | Microsoft Learn

The `AllowThreat` Windows Management Instrumentation (WMI) class method in Configuration Manager that allows the specified threat (identified by `ThreatID`) to all members in a specific collection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 AllowThreat
{
    [IN]    UInt64 ThreatID
    [IN]    String AllowSettingsUniqueID
    [IN]    String TargetCollectionID
    [OUT]   UInt32 OperationID
};
```

## Parameters

`ThreatID` Data type: `UInt64`

Qualifiers: [id("0"), in]

Threat identifier.

`AllowSettingsUniqueID` Data type: `String`

Qualifiers: [id("1"), in]

Antimalware settings (with allow threat identifier enabled) unique identifier.

`TargetCollectionID` Data type: `String`

Qualifiers: [id("2"), in]

Identifier of target collection.

`OperationID` Data type: `UInt32`

Qualifiers: [id("3"), out]

Unique identifier for the operation.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).