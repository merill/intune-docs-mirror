---
layout: Conceptual
title: IAppManagementHandler::EnforceApp - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enforceapp-method
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
description: A method that starts the installation of a specific application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7c4e1389-7575-f8e7-3f1e-242317e436ad
document_version_independent_id: d17d383b-4abf-0f8c-bc12-c3cc977cbabd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enforceapp-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enforceapp-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enforceapp-method.md
cmProducts: []
platformId: 8eb864b3-a44c-bec6-4088-745d03c7ac60
---

# IAppManagementHandler::EnforceApp - Configuration Manager | Microsoft Learn

The `IAppManagementHandler::EnforceApp` method, in Configuration Manager, starts the installation of a specific application.

If the handler supports reconnection, it must return a valid reconnect instance to `ppReconnectData`. If for whatever reason the installation cannot start, but is not in an error state, for example, no user token to display, then the handler should return `S_FALSE`.

## Syntax

```
[IDL]
HRESULT EnforceApp(
     AppAction eEnforceAction,
     HANDLE hUserToken,
     DWORD dwSessionId,
     IWbemClassObject* pHandlerSynclet,
     LPCWSTR szLocalContentPath,
     HANDLE* phInstallProcess,
     DWORD* pdwExitCode,
     LPWSTR* ppszExecutionStatus,
     IWbemClassObject** ppReconnectData
);
```

#### Parameters

`eEnforceAction` Data type: `AppAction`

Qualifiers: [in]

.

`hUserToken` Data type: `HANDLE`

Qualifiers: [in]

.

`dwSessionId` Data type: `DWORD`

Qualifiers: [in]

.

`pHandlerSynclet` Data type: `IWbemClassObject`

Qualifiers: [in]

.

`szLocalContentPath` Data type: `LPCWSTR`

Qualifiers: [in]

.

`phInstallProcess` Data type: `HANDLE`

Qualifiers: [out]

.

`pdwExitCode` Data type: `DWORD`

Qualifiers: [out]

.

`ppszExecutionStatus` Data type: `LPWSTR`

Qualifiers: [out]

.

`ppReconnectData` Data type: `IWbemClassObject`

Qualifiers: [out]

.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure. If for whatever reason the installation cannot start, but is not in an error state, for example, no user token to display UI, then the handler should return `S_FALSE`

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).