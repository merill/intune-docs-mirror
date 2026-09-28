---
layout: Conceptual
title: IAppManagementHandler::CompleteEnforcement - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--completeenforcement-method
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
description: In Configuration Manager, the IAppManagementHandler::CompleteEnforcement method completes the installation of a specific application. This method will be called only when the handler returned valid reconnection data in the EnforceApp call.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 68327579-4ef8-eac3-4e36-971461d57f89
document_version_independent_id: 7c34e43c-9c37-13b5-238d-fc714a4a76d5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--completeenforcement-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--completeenforcement-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--completeenforcement-method.md
cmProducts: []
platformId: bf904653-ea12-961d-d3c3-cf4f98911a7d
---

# IAppManagementHandler::CompleteEnforcement - Configuration Manager | Microsoft Learn

The `IAppManagementHandler::CompleteEnforcement` method, in Configuration Manager, completes the installation of a specific application. This method will be called only when the handler returned valid reconnection data in the EnforceApp call.

## Syntax

```
[IDL]
HRESULT CompleteEnforcement(
     AppAction eEnforceAction,
     IWbemClassObject* pHandlerSynclet,
     IWbemClassObject* pReconnectData,
     HANDLE hInstallProcess,
     DWORD* pdwExitCode,
     LPWSTR* ppszExecutionStatus
);
```

#### Parameters

`eEnforceAction` Data type: `AppAction`

Qualifiers: [in]

.

`pHandlerSynclet` Data type: `IWbemClassObject`

Qualifiers: [in]

.

`pReconnectData` Data type: `IWbemClassObject`

Qualifiers: [in]

.

`hInstallProcess` Data type: `HANDLE`

Qualifiers: [in]

.

`pdwExitCode` Data type: `DWORD`

Qualifiers: [out]

.

`ppszExecutionStatus` Data type: `LPWSTR`

Qualifiers: [out]

.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).