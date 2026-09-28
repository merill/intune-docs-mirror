---
layout: Conceptual
title: IAppManagementHandler::GetPendingComponentList - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--getpendingcomponentlist-method
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
description: The IAppManagementHandler::GetPendingComponentList method gets the pending component list for a specified deployment type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 94ffe54d-231e-cb37-8569-db92ab10f7c3
document_version_independent_id: 37024af0-8f4b-e483-bdaf-c6025b4c4f55
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--getpendingcomponentlist-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--getpendingcomponentlist-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--getpendingcomponentlist-method.md
cmProducts: []
platformId: f2a84541-c6f8-a3c3-2726-5bd4b8d39557
---

# IAppManagementHandler::GetPendingComponentList - Configuration Manager | Microsoft Learn

The `IAppManagementHandler::GetPendingComponentList` method, in Configuration Manager, gets the pending component list for a specified deployment type. This is an optional method for the application deployment type handler. It's called if the handler returns a status of "PendingUpdate" for the `EnforceApp` method. Software Center presents a list of these components to the end user, which need to be closed in order for the `EnforceApp` method to succeed.

## Syntax

```
[IDL]
HRESULT GetPendingComponentList(
     IWbemClassObject* pDeliveryTypeSynclet,
     LPWSTR* pwszPendingComponentList
);
```

#### Parameters

`pDeliveryTypeSynclet` Data type: `IWbemClassObject`

Qualifiers: [in]

The WMI object for the installation synclet which is associated with the application deployment type that is being installed.

`pwszPendingComponentList` Data type: `LPWSTR`

Qualifiers: [out]

The pending component list in XML format.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

E\_NOTIMPL The method isn't supported by the handler.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).