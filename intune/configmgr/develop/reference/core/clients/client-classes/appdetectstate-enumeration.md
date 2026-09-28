---
layout: Conceptual
title: AppDetectState Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appdetectstate-enumeration
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
description: Learn how to define application installation states in Configuration Manager using AppDetectState enumeration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4873cfd1-c71b-ea77-89aa-622e76e1d79f
document_version_independent_id: b590827a-7749-15ea-3185-60d7131eaacd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/appdetectstate-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/appdetectstate-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/appdetectstate-enumeration.md
cmProducts: []
platformId: c2a3a735-1102-3fcb-077a-b1b14d89a04e
---

# AppDetectState Enumeration - Configuration Manager | Microsoft Learn

In Configuration Manager, the `AppDetectState` enumeration defines application installation states. This enumeration is used by the [IAppManagementHandler Interface](iappmanagementhandler-interface).

## Syntax

```
typedef enum tagAppDetectState
{
    appDetectNotFound = 0,
    appDetectInstalled,
    appDetectFailed
}AppDetectState;

```

## Elements

`appDetectNotFound` The application was not found.

`appDetectInstalled` The application is installed.

`appDetectFailed` Application detection failed.

## Remarks

This enumeration is used by the [IAppManagementHandler Interface](iappmanagementhandler-interface).