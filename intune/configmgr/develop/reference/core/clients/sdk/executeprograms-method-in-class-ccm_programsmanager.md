---
layout: Conceptual
title: ExecutePrograms Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/executeprograms-method-in-class-ccm_programsmanager
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
description: Learn how to manage downloads of legacy software distribution programs in Configuration Manager with ExecutePrograms class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6c1845c3-46c2-c420-b685-984aa895dba9
document_version_independent_id: f59dc74d-3f3a-7dfa-0f5e-f1c3100af9e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/executeprograms-method-in-class-ccm_programsmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/executeprograms-method-in-class-ccm_programsmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/executeprograms-method-in-class-ccm_programsmanager.md
cmProducts: []
platformId: 006b67f9-ba4c-faf3-1c15-6cd9a712492a
---

# ExecutePrograms Method - Configuration Manager | Microsoft Learn

The `ExecutePrograms` WMI class method, in Configuration Manager, manages downloads of legacy software distribution programs.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 ExecutePrograms(
     [IN]  CCM_Program CCMPrograms[],
     [IN]  String SDKCallerId
);
```

#### Parameters

`CCMPrograms[]` Data type: `CCM_Program`

Qualifiers: [in]

Array of software distribution programs to download.

`SDKCallerId` Data type: `String`

Qualifiers: [in]

Identifier of the caller.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).