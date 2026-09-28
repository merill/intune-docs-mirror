---
layout: Conceptual
title: IAppManagementHandler::CheckReconnectData - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--checkreconnectdata-method
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
description: In Configuration Manager, the IAppManagementHandler::CheckReconnectData method checks whether the reconnection data is valid.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1be51296-4571-10e1-f687-bb64407199bf
document_version_independent_id: 794ee897-28b0-ba24-aaa0-146e80e5f248
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--checkreconnectdata-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--checkreconnectdata-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--checkreconnectdata-method.md
cmProducts: []
platformId: b48b7c96-5208-46e9-d4b2-be3beffc1edc
---

# IAppManagementHandler::CheckReconnectData - Configuration Manager | Microsoft Learn

The `IAppManagementHandler::CheckReconnectData` method, in Configuration Manager, checks whether the reconnection data is valid.

## Syntax

```
[IDL]
HRESULT CheckReconnectData(
     IWbemClassObject* pReconnectData,
     BOOL* pfIsValid,
     BOOL* pfEnforcementFinished
);
```

#### Parameters

`pReconnectData` Data type: `IWbemClassObject`

Qualifiers: [in]

.

`pfIsValid` Data type: `BOOL`

Qualifiers: [out]

.

`pfEnforcementFinished` Data type: `BOOL`

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