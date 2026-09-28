---
layout: Conceptual
title: IsWindowAvailableNow Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/iswindowavailablenow-method-in-class-ccm_servicewindowmanager
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
description: Learn how to determine if a service window of a specified type and duration is available to run using IsWindowAvailableNow.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c42bb57d-71fd-a92c-e71b-908f95ccdfd7
document_version_independent_id: ab0f4e3a-2bdd-df48-7107-8fd0a914e059
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/iswindowavailablenow-method-in-class-ccm_servicewindowmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/iswindowavailablenow-method-in-class-ccm_servicewindowmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/iswindowavailablenow-method-in-class-ccm_servicewindowmanager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 81023bc5-c5b6-826b-96cd-53a6644b75f3
---

# IsWindowAvailableNow Method - Configuration Manager | Microsoft Learn

The `IsWindowAvailableNow` WMI class method, in Configuration Manager, determines whether a service window of a specified type and the given duration is available to run at the point of time when the call is made.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 IsWindowAvailableNow(
     [IN]  UInt32 ServiceWindowType,
     [IN]  Boolean FallbackToAllProgramsWindow,
     [IN]  UInt32 MaxRuntime,
     [OUT] Boolean CanProgramRunNow
);
```

#### Parameters

`ServiceWindowType` Data type: `UInt32`

Qualifiers: [in]

Type of service window. The following table lists possible values.

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

`true`, if the generic **All programs window** service window is to be used when a window specified in `FallbackToAllProgramsWindow` is not available; otherwise, `false`.

`MaxRuntime` Data type: `UInt32`

Qualifiers: [in]

Maximum run time, in minutes, that a software update installation has to complete before the installation is no longer monitored by Configuration Manager. This setting is also used to determine whether there is enough time to install the update before the end of a maintenance window. The default setting is 60 minutes for service packs and 5 minutes for all other software update types. Values can range from 5 to 9999 minutes.

Important

Make sure that the maximum run time value is not set for more time than the configured maintenance window or the software update installation will not initiate.

`CanProgramRunNow` Data type: `Boolean`

Qualifiers: [out]

`true` if a service window of the specified type and the given duration is available to run at the point of time when the call is made; otherwise, `false`.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).