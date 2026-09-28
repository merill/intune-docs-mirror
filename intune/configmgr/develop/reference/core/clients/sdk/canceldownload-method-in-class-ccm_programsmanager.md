---
layout: Conceptual
title: CancelDownload method in class CCM_ProgramsManager - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_programsmanager
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
description: Learn how the CancelDownload WMI class method, in Configuration Manager, cancels jobs that are downloading content that is required for legacy software distribution programs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7028fd89-dbf4-abd2-08eb-8fe6ce2eac6c
document_version_independent_id: d063992a-1770-090b-1601-bb1b5b987ce0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_programsmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_programsmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_programsmanager.md
cmProducts: []
platformId: 5999c8df-91ef-9a3f-89f9-427658f32907
---

# CancelDownload method in class CCM_ProgramsManager - Configuration Manager | Microsoft Learn

The `CancelDownload` WMI class method, in Configuration Manager, cancels jobs that are downloading content that is required for legacy software distribution programs.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 CancelDownload(
     [IN]  String ProgramID,
     [IN]  String PackageID
);
```

#### Parameters

`ProgramID` Data type: `String`

Qualifiers: [in]

Identifier of the software distribution program.

`PackageID` Data type: `String`

Qualifiers: [in]

Identifier of the associated software distribution package.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).