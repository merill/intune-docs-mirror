---
layout: Conceptual
title: CheckSourceFolder Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/checksourcefolder-method-in-class-sms_driverpackage
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
description: Learn how to check the state of an empty driver source folder with CheckSourceFolder class im Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 74719af0-2708-b3e1-1786-ca33a87783a8
document_version_independent_id: bc92e2a0-2909-3124-fa3c-7c437ef5fefb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/checksourcefolder-method-in-class-sms_driverpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/checksourcefolder-method-in-class-sms_driverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/checksourcefolder-method-in-class-sms_driverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 03b7c72e-65e5-4200-cb68-60ae7391cbfe
---

# CheckSourceFolder Method - Configuration Manager | Microsoft Learn

The `CheckSourceFolder` Windows Management Instrumentation (WMI) class method in Configuration Manager that checks the state of an empty driver source folder.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 CheckSourceFolder
{
    [IN]    String SourceFolder
    [OUT]   SInt32 Result
};
```

## Parameters

`SourceFolder` Data type: `String`

Qualifiers: [id("0"), in]

Source folder.

`Result` Data type: `SInt32`

Qualifiers: [id("1"), out]

Results of check. Possible values are:

| Value | Result |
| --- | --- |
| 0 | No error. |
| 1 | The folder isn't in UNC format. |
| 2 | Can't read/write to the folder. |
| 4 | The folder isn't empty. |
| 8 | The folder is already used by another driver package. |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).