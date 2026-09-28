---
layout: Conceptual
title: AddSoftwareHashData Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/addsoftwarehashdata-method-in-class-sms_aisoftwarelist
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
description: Learn how to add the SoftwarePropertiesHash from SoftwareCode and Title in Configuration Manager using the AddSoftwareHashData class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9e48931e-8d23-090e-9e59-e28b82694a82
document_version_independent_id: 54f451e6-91a7-758f-8ecb-ae3633986365
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/addsoftwarehashdata-method-in-class-sms_aisoftwarelist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/addsoftwarehashdata-method-in-class-sms_aisoftwarelist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/addsoftwarehashdata-method-in-class-sms_aisoftwarelist.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 34a0e1fb-3aeb-d866-7652-ef632afac2f8
---

# AddSoftwareHashData Method - Configuration Manager | Microsoft Learn

The `AddSoftwareHashData` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds the `SoftwarePropertiesHash` from `SoftwareCode` and `Title`.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddSoftwareHashData(
     UInt32 SoftwareTitles,
     UInt32 SoftwareHashs
);
```

#### Parameters

`SoftwareTitles` Data type: `UInt32`

Qualifiers: [out]

Count of software titles inserted during this method call.

`SoftwareHashs` Data type: `UIn32`

Qualifiers: [out]

Count of software hashes inserted during this method call.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).