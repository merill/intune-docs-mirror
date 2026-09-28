---
layout: Conceptual
title: Uninstall Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/uninstall-method-in-class-ccm_application
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
description: Learn how to uninstall an application using the Uninstall Windows Management Instrumentation (WMI) class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e95ad09b-9e47-131f-44be-cbe8f06ec158
document_version_independent_id: 358fc476-b3e4-3d5d-cfdd-7084613de7e4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/uninstall-method-in-class-ccm_application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/uninstall-method-in-class-ccm_application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/uninstall-method-in-class-ccm_application.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 13ce25d7-d2cd-b30b-2259-e59755ddb41c
---

# Uninstall Method - Configuration Manager | Microsoft Learn

The `Uninstall` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that uninstalls an application.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 Uninstall
{
    [IN]    String Id
    [IN]    String Revision
    [IN]    Boolean IsMachineTarget
    [IN]    UInt32 EnforcePreference
    [IN]    String Priority
    [IN]    Boolean IsRebootIfNeeded
    [OUT]   String JobId
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: [id("0"), in]

Application identifier.

`Revision` Data type: `String`

Qualifiers: [id("1"), in]

Revision.

`IsMachineTarget` Data type: `Boolean`

Qualifiers: [id("2"), in]

`true` if the application targets a machine.

`EnforcePreference` Data type: `UInt32`

Qualifiers: [id("3"), in, values]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | NonBusinessHours |
| 2 | AdminSchedule |

`Priority` Data type: `String`

Qualifiers: [id("4"), in, valuemap]

Priority. Possible values are:

| Value |
| --- |
| Foreground |
| High |
| Normal |
| Low |

`IsRebootIfNeeded` Data type: `Boolean`

Qualifiers: [id("5"), in]

`true` if a reboot is needed.

`JobId` Data type: `String`

Qualifiers: [id("6"), out]

Job identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).