---
layout: Conceptual
title: AllowAccess Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/allowaccess-method-in-class-sms_devicemethods
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn about the simplified syntax, parameters, return values, and requirement of the AllowAccess method.
locale: en-us
document_id: bb415ab6-f28a-b8e1-e348-4f3fd5c980d4
document_version_independent_id: 96ccf2d1-c8d6-0864-a1e6-4e3a36a8207a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/allowaccess-method-in-class-sms_devicemethods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/allowaccess-method-in-class-sms_devicemethods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/allowaccess-method-in-class-sms_devicemethods.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fe16a0df-477f-0980-132c-2cc62bda5eb8
---

# AllowAccess Method - Configuration Manager | Microsoft Learn

The `AllowAccess` Windows Management Instrumentation (WMI) class method, in Configuration Manager, lets the Exchange ActiveSync device connect to Exchange.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AllowAccess(
   UInt32 ResourceId
   String EASIdentities[]
);
```

#### Parameters

`ResourceId` Data type: `UInt32`

Qualifiers: [in]

ID of the resource.

`EASIdentities` Data type: `String` Array

Qualifiers: [in]

Array of Exchange ActiveSync identities.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements