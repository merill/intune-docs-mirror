---
layout: Conceptual
title: SetAllUpdatesUserExperience Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager
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
description: In Configuration Manager, the SetAllUpdatesUserExperience WMI class method sets the user experience mode that determines how software updates are displayed on a target computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fc8dddec-138e-c2ba-8335-e48091dadd2f
document_version_independent_id: a09a600b-8500-0740-927c-53aa63dbce38
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager.md
cmProducts: []
platformId: a860401d-bbca-f05a-a2f1-aee725d76c59
---

# SetAllUpdatesUserExperience Method - Configuration Manager | Microsoft Learn

The `SetAllUpdatesUserExperience` WMI class method, in Configuration Manager, sets the user experience mode that determines how software updates are displayed on a target computer.

Note

This method can be used to hide or show all software updates in software center.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 SetAllUpdatesUserExperience(
     [IN]  UInt32 UserExperience
);
```

#### Parameters

`UserExperience` Data type: `UInt32`

Qualifiers: [in]

The user experience flag. The following table shows the possible user experience mode values.

| Value | User experience |
| --- | --- |
| 0 | DEFAULT (per policy) |
| 1 | INTERACTIVE |
| 2 | QUIET |

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

This method is only available for local administrators. When a software update deployment has been prepared and software updates are available for installation, this method and the `GetAllUpdatesUserExperience` method can be used to configure the user experience.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).