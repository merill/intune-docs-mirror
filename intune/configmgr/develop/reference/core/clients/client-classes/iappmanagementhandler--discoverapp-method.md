---
layout: Conceptual
title: IAppManagementHandler::DiscoverApp - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--discoverapp-method
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
description: Learn how to run a synchronous discovery operation for the provided synclet using IAppManagementHandler::DiscoveryApp.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ebbf5597-f444-8b67-6c0d-155584e840cf
document_version_independent_id: ec04a4ca-d0e0-1397-b8b0-753fff710713
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--discoverapp-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--discoverapp-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--discoverapp-method.md
cmProducts: []
platformId: 77a0ad29-c96f-a60d-9dd3-a72029d2be02
---

# IAppManagementHandler::DiscoverApp - Configuration Manager | Microsoft Learn

The `IAppManagementHandler::DiscoverApp` method, in Configuration Manager, runs a synchronous discovery operation for the provided synclet.

## Syntax

```
[IDL]
HRESULT DiscoverApp(
     HANDLE hUserToken,
     LPCWSTR szDeploymentTypeId,
     DWORD dwDeploymentTypeRevision,
     AppDeploymentTypeData* pDetectResult
);
```

#### Parameters

`hUserToken` Data type: `HANDLE`

Qualifiers: [in]

The user token. If it's null, the action is for computer. If it isn't NULL, the action is for the user.

`szDeploymentTypeId` Data type: `DWORD`

Qualifiers: [in]

.

`dwDeploymentTypeRevision` Data type: `DWORD`

Qualifiers: [in]

.

`pDetectResult` Data type: `AppDeploymentTypeData`

Qualifiers: [out]

.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).