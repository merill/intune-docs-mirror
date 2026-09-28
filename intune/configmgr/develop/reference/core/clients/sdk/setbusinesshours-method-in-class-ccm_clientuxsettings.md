---
layout: Conceptual
title: SetBusinessHours Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setbusinesshours-method-in-class-ccm_clientuxsettings
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
description: Learn how the SetBusinessHours Windows Management Instrumentation (WMI) class method in Configuration Manager that sets the values for business hours.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0eb37dfc-26ae-1b91-4589-f55fc6f4db87
document_version_independent_id: f0d59d6d-d537-68d1-cd84-914af5d0f991
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/setbusinesshours-method-in-class-ccm_clientuxsettings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/setbusinesshours-method-in-class-ccm_clientuxsettings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/setbusinesshours-method-in-class-ccm_clientuxsettings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4909a9b5-b350-6d0d-388d-74f6644bf283
---

# SetBusinessHours Method - Configuration Manager | Microsoft Learn

The `SetBusinessHours` Windows Management Instrumentation (WMI) class method in Configuration Manager that sets the values for business hours.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 SetBusinessHours
{
    [IN]    UInt32 WorkingDays
    [IN]    UInt32 StartTime
    [IN]    UInt32 EndTime
};
```

## Parameters

`WorkingDays` Data type: `UInt32`

Qualifiers: [id("0"), in]

Working days.

`StartTime` Data type: `UInt32`

Qualifiers: [id("1"), in]

Start time.

`EndTime` Data type: `UInt32`

Qualifiers: [id("2"), in]

End time.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).