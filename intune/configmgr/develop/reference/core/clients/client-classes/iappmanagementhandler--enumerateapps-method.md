---
layout: Conceptual
title: IAppManagementHandler::EnumerateApps - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enumerateapps-method
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
description: Learn how to run a synchronous discovery operation for the provided synclet in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3f1e6e08-b2a3-caf2-3bb1-56cbe8d927c4
document_version_independent_id: 63a32ab3-026e-a3b2-2e99-78e49cb38e64
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enumerateapps-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enumerateapps-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enumerateapps-method.md
cmProducts: []
platformId: 2f2a32e3-f437-8042-45b1-5445e42775ec
---

# IAppManagementHandler::EnumerateApps - Configuration Manager | Microsoft Learn

The `IAppManagementHandler::EnumerateApps` method, in Configuration Manager, runs a synchronous discovery operation for the provided synclet.

## Syntax

```
[IDL]
HRESULT EnumerateApps(
     HANDLE hUserToken,
     AppDeploymentTypeData* pDetectResult
);
```

#### Parameters

`hUserToken` Data type: `HANDLE`

Qualifiers: [in]

The user token. If it's null, the action is for computer. If it isn't NULL, the action is for the user.

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