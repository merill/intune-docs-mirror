---
layout: Conceptual
title: PostponeProgramsToNonBusinessHours Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager
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
description: In Configuration Manager, the PostponeProgramsToNonBusinessHours WMI class method schedules legacy software distribution programs to run in the next available user defined service window.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3d30ef52-0949-2f0d-df61-2716880889a5
document_version_independent_id: 0aa4ce52-50aa-4114-e919-319de98ab50c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bfc5baeb-a5f4-758d-89df-0c8b90a0c357
---

# PostponeProgramsToNonBusinessHours Method - Configuration Manager | Microsoft Learn

The `PostponeProgramsToNonBusinessHours` WMI class method, in Configuration Manager, schedules legacy software distribution programs to run in the next available user defined service window.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 PostponeProgramsToNonBusinessHours(
     [IN]  CCM_Program CCMPrograms[],
     [IN]  Boolean RebootImmediatelyAfterInstall
);
```

#### Parameters

`CCMPrograms []` Data type: `CCM_Program`

Qualifiers: [in]

Array of software distribution programs to be postponed.

`RebootImmediatelyAfterInstall` Data type: `Boolean`

Qualifiers: [in]

`true` if the computer restarts immediately after the installation, otherwise, `false`.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).