---
layout: Conceptual
title: GetDependency method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/getdependency-method-in-class-sms_collection
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
description: Get the collection relationship info which the input collection depends on.
ms.date: 2020-11-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7f4849ce-c0c1-bced-8411-546ff8633592
document_version_independent_id: 0164a175-3d96-6b5c-c857-ff7aeeed5e54
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/getdependency-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/getdependency-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/getdependency-method-in-class-sms_collection.md
cmProducts: []
platformId: 5e012500-3d84-6436-a4ea-ee8bfb10eff5
---

# GetDependency method - Configuration Manager | Microsoft Learn

Starting in version 2010, the `GetDependency` WMI class method in Configuration Manager gets the collection relationship info which the input collection depends on.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```MOF
sint32 GetDependency(
    string Relationship[]
);
```

## Parameters

### `Relationship`

Data type: `String[]` (array)

Qualifiers: [out]

JSON string array of collection dependency relationship.

## Return values

An `SInt32` data type that is `0` to indicate success, or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).