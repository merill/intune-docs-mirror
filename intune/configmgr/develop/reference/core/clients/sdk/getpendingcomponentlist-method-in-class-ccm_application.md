---
layout: Conceptual
title: GetPendingComponentList Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getpendingcomponentlist-method-in-class-ccm_application
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
description: In Configuration Manager, the GetPendingComponentList Windows Management Instrumentation class method that gets the pending component list for an application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 328a4683-da2e-314a-69bc-6b22f5910939
document_version_independent_id: 7687651a-7dbc-1ca8-b77f-598ce4e4eb7e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getpendingcomponentlist-method-in-class-ccm_application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getpendingcomponentlist-method-in-class-ccm_application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getpendingcomponentlist-method-in-class-ccm_application.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c6a6e090-f2b8-49a8-5a5c-01791b89b771
---

# GetPendingComponentList Method - Configuration Manager | Microsoft Learn

The `GetPendingComponentList` Windows Management Instrumentation (WMI) class method in Configuration Manager that gets the pending component list for an application.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetPendingComponentList
{
    [IN]    String AppDeliveryTypeId
    [IN]    UInt32 Revision
    [OUT]   String PendingComponentList
};
```

## Parameters

`AppDeliveryTypeId` Data type: `String`

Qualifiers: [id("0"), in]

Application delivery type identifier.

`Revision` Data type: `UInt32`

Qualifiers: [id("1"), in]

Revision.

`PendingComponentList` Data type: `String`

Qualifiers: [id("2"), out]

Pending component list.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).