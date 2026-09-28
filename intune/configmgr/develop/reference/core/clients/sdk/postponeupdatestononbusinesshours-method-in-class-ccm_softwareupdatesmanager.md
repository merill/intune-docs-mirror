---
layout: Conceptual
title: PostponeUpdatesToNonBusinessHours Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/postponeupdatestononbusinesshours-method-in-class-ccm_softwareupdatesmanager
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
description: Learn how to postpone a set of software updates to automatically install in specified non-business hours.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 597aed3b-8331-3f7d-9981-4c443090c90a
document_version_independent_id: 57de1a0c-292f-90ec-775c-5ec6af7f0c4d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/postponeupdatestononbusinesshours-method-in-class-ccm_softwareupdatesmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/postponeupdatestononbusinesshours-method-in-class-ccm_softwareupdatesmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/postponeupdatestononbusinesshours-method-in-class-ccm_softwareupdatesmanager.md
cmProducts: []
platformId: 0d1eff49-c76f-377c-e55f-44ef94a4ca11
---

# PostponeUpdatesToNonBusinessHours Method - Configuration Manager | Microsoft Learn

The `PostoneUpdatesToNonBusinessHours` WMI class method, in Configuration Manager, postpones a set of software updates to automatically install in non-business hours, which are specified by the user.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 PostponeUpdatesToNonBusinessHours(
     [IN]  CCM_SoftwareUpdate CCMUpdates[],
     [IN]  Boolean RebootImmediatelyAfterInstall
);
```

#### Parameters

`CCMUpdates[]` Data type: `CCM_SoftwareUpdate`

Qualifiers: [in]

Array of software updates to be installed.

`RebootImmediatelyAfterInstall` Data type: `Boolean`

Qualifiers: [in]

`true` if the computer restarts immediately after the installation; otherwise, `false`.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).