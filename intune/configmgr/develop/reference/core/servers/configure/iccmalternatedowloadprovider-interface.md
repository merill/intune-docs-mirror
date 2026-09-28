---
layout: Conceptual
title: ICcmAlternateDownloadProvider Interface - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedowloadprovider-interface
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
description: Learn how to use the ICcmAlternateDownloadProvider Interface to define the interface for an alternative download provider to be invoked by Content Transfer Manager to download packages.
ms.date: 2017-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 44d38b2f-f970-8d2f-6c69-cc1302c44a67
document_version_independent_id: 304830bf-1868-6f9b-1513-29342badd909
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedowloadprovider-interface.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedowloadprovider-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedowloadprovider-interface.md
cmProducts: []
platformId: d78be2b6-41ff-764a-fda9-bdfe5b49e330
---

# ICcmAlternateDownloadProvider Interface - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider** interface, in Configuration Manager, defines the interface for an alternative download provider to be invoked by Content Transfer Manager to download packages.

## Syntax

```
[
    uuid(89F7454D-71F7-4F05-8276-FADC8B85F48D),
    object,
    pointer_default(unique)
]

```

## Methods

The **ICcmAlternateDownloadProvider** interface defines the following methods.

| Method | Description |
| --- | --- |
| [ICcmAlternatedownloadProvider : CancelJob Method](iccmalternatedownloadprovider---canceljob-method) | Cancels a job. |
| [ICcmAlternatedownloadProvider : DownloadContent Method](iccmalternatedownloadprovider---downloadcontent-method) | Instructs the provider to download content. |
| [ICcmAlternatedownloadProvider : ModifyJobSource Method](iccmalternatedownloadprovider---modifyjobsource-method) | Instructs the provider to modify the source location for a given job. |
| [ICcmAlternatedownloadProvider : ModifyJobPriority Method](iccmalternatedownloadprovider---modifyjobpriority-method) | Instructs the provider to modify the priority for a given job. |
| [ICcmAlternatedownloadProvider : ModifyJobTimeout Method](iccmalternatedownloadprovider---modifyjobtimeout-method) | Instructs the provider to modify the timeout for a given job. |
| [ICcmAlternatedownloadProvider : Resume Method](iccmalternatedownloadprovider---resume-method) | Instructs the provider to resume a given job. |
| [ICcmAlternatedownloadProvider : Suspend Method](iccmalternatedownloadprovider---suspend-method) | Suspends a given job. |

## Remarks

ISVs should implement this interface and create an instance of local CCM\_DownloadProvider policy that corresponds to their implementation.

Important

This interface must be implemented out-of-process from ccmexec.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).