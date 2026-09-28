---
layout: Conceptual
title: CIJobState Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration
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
description: Learn how CIJobState enumeration defines configuration item agent job states and is used by ICIINFO Interface.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b3998fca-7929-5cf6-8d06-d3be29b8f362
document_version_independent_id: 5da5f6da-6ce3-7e46-9347-5c9c3a1b090d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 70f202a5-2674-c34b-8aa7-447205c48d8b
---

# CIJobState Enumeration - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CIJobState` enumeration defines configuration item agent job states. This enumeration is used by the [ICIINFO Interface](iciinfo-interface).

## Syntax

```
typedef enum tagCIJobState
{
  ciJobStateNone = 0,
  ciJobStateAvailable,
  ciJobStateSubmitted,
  ciJobStateDetecting,
  ciJobStateDownloadingCIDef,
  ciJobStateDownloadingSdmPkg,
  ciJobStatePreDownload,
  ciJobStateDownloading,
  ciJobStateWaitInstall,
  ciJobStateInstalling,
  ciJobStatePendingSoftReboot,
  ciJobStatePendingHardReboot,
  ciJobStateWaitReboot,
  ciJobStateVerifying,
  ciJobStateInstallComplete,
  ciJobStateError,
  ciJobStateWaitServiceWindow
} CIJobState;
```

## Elements

`ciJobStateNone` No state.

`ciJobStateAvailable` Available.

`ciJobStateSubmitted` Submitted.

`ciJobStateDetecting` Being detected.

`ciJobStateDownloadingCIDef` Downloading configuration item definition.

`ciJobStateDownloadingSdmPkg` Downloading a System Definition Model (SDM) package.

`ciJobStatePreDownload` Pre-download.

`ciJobStateDownloading` Downloading.

`ciJobStateWaitInstall` Wait for installation.

`ciJobStateInstalling` Installing.

`ciJobStatePendingSoftReboot` Suspend operation for soft reboot.

`ciJobStatePendingHardReboot` Suspend operation for hard reboot.

`ciJobStateWaitReboot` Wait for reboot.

`ciJobStateVerifying` Verifying.

`ciJobStateInstallComplete` Installation complete.

`ciJobStateError` Error.

`ciJobStateWaitServiceWindow` Wait for maintenance window.