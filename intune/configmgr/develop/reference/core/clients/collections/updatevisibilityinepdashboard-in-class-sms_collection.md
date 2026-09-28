---
layout: Conceptual
title: UpdateVisibilityInEPDashBoard Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/updatevisibilityinepdashboard-in-class-sms_collection
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
description: In Configuration Manager, the UpdateVisibilityInEPDashBoard Windows Management Instrumentation class method that shows this collection in the Endpoint Protection dashboard.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fdfdd35f-c3b2-a92e-ed69-91b7cefea140
document_version_independent_id: 87182a0c-3bb9-4ee4-9a4e-4d97093ac252
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/updatevisibilityinepdashboard-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/updatevisibilityinepdashboard-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/updatevisibilityinepdashboard-in-class-sms_collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f9446195-e15a-8595-cd8b-d36110ec95d3
---

# UpdateVisibilityInEPDashBoard Method - Configuration Manager | Microsoft Learn

The `UpdateVisibilityInEPDashBoard` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that shows this collection in the Endpoint Protection dashboard.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 UpdateVisibilityInEPDashBoard
{
    [IN]    Boolean Visible
};
```

## Parameters

`Visible` Data type: `Boolean`

Qualifiers: [id("0"), in]

`true` if this collection should show in the Endpoint Protection dashboard.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).