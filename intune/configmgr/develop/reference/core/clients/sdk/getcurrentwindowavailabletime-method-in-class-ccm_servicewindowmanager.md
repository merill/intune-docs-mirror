---
layout: Conceptual
title: GetCurrentWindowAvailableTime Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager
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
description: Learn how the GetCurrentWindowAvailableTime WMI class method, in Configuration Manager, gets the time remaining in a currently active service window for a specified type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 51f35359-d0e7-6aac-a541-c9b2f5b14fb1
document_version_independent_id: 910fc7f5-d67c-1b9d-698c-73c08a9893e2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3b6b9704-3eb7-2fc5-a62b-27a7eaad777a
---

# GetCurrentWindowAvailableTime Method - Configuration Manager | Microsoft Learn

The `GetCurrentWindowAvailableTime` WMI class method, in Configuration Manager, gets the time remaining in a currently active service window for a specified type.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetCurrentWindowAvailableTime(
     [IN]  UInt32 ServiceWindowType,
     [IN]  Boolean FallbackToAllProgramsWindow,
     [OUT] UInt32 WindowAvailableTime
);
```

#### Parameters

`ServiceWindowType` Data type: `UInt32`

Qualifiers: [in]

Type of service window. The following table shows the list of possible values.

| Value | Service Window Type | Description |
| --- | --- | --- |
| 1 | ALLPROGRAM\_SERVICEWINDOW | All Programs Service Window |
| 2 | PROGRAM\_SERVICEWINDOW | Program Service Window |
| 3 | REBOOTREQUIRED\_SERVICEWINDOW | Reboot Required Service Window |
| 4 | SOFTWAREUPDATE\_SERVICEWINDOW | Software Update Service Window |
| 5 | OSD\_SERVICEWINDOW | OSD Service Window |
| 6 | USER\_DEFINED\_SERVICE\_WINDOW | Corresponds to non-working hours |

`FallbackToAllProgramsWindow` Data type: `Boolean`

Qualifiers: [in]

`true` if the generic **All programs window** service window is to be used when a window specified in `ServiceWindowType` is not available; otherwise, `false`.

`WindowAvailableTime` Data type: `UInt32`

Qualifiers: [out]

Available time remaining for service window.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).