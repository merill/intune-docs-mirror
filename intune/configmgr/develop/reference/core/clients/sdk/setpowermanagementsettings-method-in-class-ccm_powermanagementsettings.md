---
layout: Conceptual
title: SetPowerManagementSettings Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setpowermanagementsettings-method-in-class-ccm_powermanagementsettings
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
description: A class method that sets power management settings on a client.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5b727267-9bdb-9d1e-5f40-c65836446058
document_version_independent_id: 53385793-bf8b-d266-d19b-7a49892f279e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/setpowermanagementsettings-method-in-class-ccm_powermanagementsettings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/setpowermanagementsettings-method-in-class-ccm_powermanagementsettings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/setpowermanagementsettings-method-in-class-ccm_powermanagementsettings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 987aec0f-dbff-1abb-d623-6ffbbd552fa2
---

# SetPowerManagementSettings Method - Configuration Manager | Microsoft Learn

The `SetPowerManagementSettings` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that sets power management settings on a client.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 SetPowerManagementSettings
{
    [IN]  Boolean IsOptOutFromPowerPlan;
    [OUT] UInt32 ReturnValue;
};
```

## Parameters

`IsOptOutFromPowerPlan` Data type: `Boolean`

Qualifiers: [id("0"), in]

`true` to allow users to exclude their device from power management.

`ReturnValue` Data type: `UInt32`

Qualifiers: [out]

Return value.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).