---
layout: Conceptual
title: GetDependent method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/getdependent-method-in-class-sms_collection
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
description: Get the collection relationship info which depends on the input collection.
ms.date: 2020-11-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 155b5b6e-468d-0a8a-4f55-e8c0b94b511c
document_version_independent_id: 3217d086-48aa-39ab-cb36-af1035fbcb03
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/getdependent-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/getdependent-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/getdependent-method-in-class-sms_collection.md
cmProducts: []
platformId: a81f6235-2fb0-f34d-f96e-6bada43c329d
---

# GetDependent method - Configuration Manager | Microsoft Learn

Starting in version 2010, the `GetDependent` WMI class method in Configuration Manager gets the collection relationship info which depends on the input collection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```MOF
sint32 GetDependent(
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