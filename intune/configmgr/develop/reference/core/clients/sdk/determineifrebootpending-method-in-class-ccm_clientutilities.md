---
layout: Conceptual
title: DetermineIfRebootPending Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/determineifrebootpending-method-in-class-ccm_clientutilities
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how DetermineIfRebootPending is simplified from Managed Object Format code and defines the method.
locale: en-us
document_id: a3dc3ba7-f769-814c-5c1a-6528fad2afca
document_version_independent_id: e89138ef-e6e4-17a2-e4d3-5e94575d852b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/determineifrebootpending-method-in-class-ccm_clientutilities.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/determineifrebootpending-method-in-class-ccm_clientutilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/determineifrebootpending-method-in-class-ccm_clientutilities.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d087f8ff-dcd6-c3d3-a17a-898868e70b44
---

# DetermineIfRebootPending Method - Configuration Manager | Microsoft Learn

The `DetermineIfRebootPending` Windows Management Instrumentation (WMI) class method in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 DetermineIfRebootPending
{
    [OUT]   Boolean RebootPending
    [OUT]   Boolean IsHardRebootPending
    [OUT]   Boolean InGracePeriod
    [OUT]   DateTime DisableHideTime
    [OUT]   DateTime RebootDeadline
};
```

## Parameters

`RebootPending` Data type: `Boolean`

Qualifiers: [id("0"), out]

RebootPending.

`IsHardRebootPending` Data type: `Boolean`

Qualifiers: [id("1"), out]

IsHardRebootPending.

`InGracePeriod` Data type: `Boolean`

Qualifiers: [id("2"), out]

InGracePeriod.

`DisableHideTime` Data type: `DateTime`

Qualifiers: [id("3"), out]

DisableHideTime.

`RebootDeadline` Data type: `DateTime`

Qualifiers: [id("4"), out]

RebootDeadline.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).