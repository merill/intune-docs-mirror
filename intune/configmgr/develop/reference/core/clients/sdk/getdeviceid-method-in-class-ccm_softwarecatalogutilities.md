---
layout: Conceptual
title: GetDeviceId Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getdeviceid-method-in-class-ccm_softwarecatalogutilities
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
description: Learn how to use the GetDeviceId method to return the device (client) identifier.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a019dead-8ecb-97d6-8d9a-8e28f73d61b8
document_version_independent_id: 5ae96622-c4ad-fc01-d950-a771ef6f1089
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getdeviceid-method-in-class-ccm_softwarecatalogutilities.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getdeviceid-method-in-class-ccm_softwarecatalogutilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getdeviceid-method-in-class-ccm_softwarecatalogutilities.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ef776d53-e686-ef55-cd79-29c08ee3e2da
---

# GetDeviceId Method - Configuration Manager | Microsoft Learn

The `GetDeviceId` Windows Management Instrumentation (WMI) class method in Configuration Manager that returns the device (client) identifier.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetDeviceId
{
    [OUT]   String ClientId
    [OUT]   String SignedClientId
};
```

## Parameters

`ClientId` Data type: `String`

Qualifiers: [id("0"), out]

Client identifier.

`SignedClientId` Data type: `String`

Qualifiers: [id("1"), out]

Signed client identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).