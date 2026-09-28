---
layout: Conceptual
title: GetAllUpdatesUserExperience Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager
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
description: Learn how to get the user experience mode that determines how software updates are displayed with GetAllUpdatesUserExperience.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 046da033-1882-b84e-6738-2447a035fea4
document_version_independent_id: 774bc040-aa24-9f43-2e5f-b5c77ab04be0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager.md
cmProducts: []
platformId: 46c9ad93-ad98-a197-443e-ba48bcaa56a4
---

# GetAllUpdatesUserExperience Method - Configuration Manager | Microsoft Learn

The `GetAllUpdatesUserExperience` WMI class method, in Configuration Manager, gets the user experience mode that determines how software updates are displayed on a target computer.

Note

This method can be used to hide or show all software updates in software center.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 GetAllUpdatesUserExperience(
     [OUT] UInt32 UserExperience
);
```

#### Parameters

`UserExperience` Data type: `UInt32`

Qualifiers: [out]

The user experience mode. The following table shows the possible user experience mode values.

| Value | User experience |
| --- | --- |
| 0 | DEFAULT (per policy) |
| 1 | INTERACTIVE |
| 2 | QUIET |

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

This method is only available for local administrators. When a software update deployment has been prepared and software updates are available for installation, this method and the `SetAllUpdatesUserExperience` method can be used to configure the user experience.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).