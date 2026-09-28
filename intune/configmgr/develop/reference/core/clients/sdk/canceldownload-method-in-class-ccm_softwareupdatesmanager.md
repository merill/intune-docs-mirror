---
layout: Conceptual
title: CancelDownload method in class CCM_SoftwareUpdatesManager - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_softwareupdatesmanager
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
description: Learn how to cancel an in-progress download of software updates during a deployment using the CancelDownload class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f22d2574-0168-dd98-51a8-38882987f436
document_version_independent_id: 3086bc44-cfbd-2476-dee8-7d34c0a61d08
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_softwareupdatesmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_softwareupdatesmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_softwareupdatesmanager.md
cmProducts: []
platformId: 07a322dd-cd66-91cb-c0c4-01b588de2df6
---

# CancelDownload method in class CCM_SoftwareUpdatesManager - Configuration Manager | Microsoft Learn

The `CancelDownload` WMI class method, in Configuration Manager, cancels an in-progress download of software updates during a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 CancelDownload();
```

#### Parameters

None.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

The `CancelDownload` method cancels the download only for deployments that are initiated by the Software Updates Client Agent or through the Configuration Manager SDK. If the software updates deployment was initiated as the result of a deadline, the call to this method fails.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).