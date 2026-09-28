---
layout: Conceptual
title: SetIgnorePrereqWarning Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/setignoreprereqwarning-method-in-class-sms_cm_updatepackages
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
description: The SetIgnorePrereqWarning Windows Management Instrumentation class method, in Configuration Manager, updates the ignore prerequisites warning flag of the update packages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b6ab88d3-4cde-31a5-a26c-f55c7b862972
document_version_independent_id: aa2f3013-57c3-28b5-be0f-0c84638f5304
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/setignoreprereqwarning-method-in-class-sms_cm_updatepackages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/setignoreprereqwarning-method-in-class-sms_cm_updatepackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/setignoreprereqwarning-method-in-class-sms_cm_updatepackages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b3da473c-ee99-748d-39e7-4b3897d07d9f
---

# SetIgnorePrereqWarning Method - Configuration Manager | Microsoft Learn

The `SetIgnorePrereqWarning` Windows Management Instrumentation (WMI) class method in Configuration Manager updates the ignore prerequisites warning flag of the update packages.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method:

## Syntax

```
SInt32 SetIgnorePrereqWarning(
     UInt32 flag
);

```

#### Parameters

`flag` Data type: `UInt32`

Qualifiers: [in]

Flag to ignore the prerequisites warning flag of the update packages. Possible values are:

| Value | Flag |
| --- | --- |
| 0 | NOT\_CONTINUE\_ON\_PREREQ\_WARNING. During installation, stop the upgrade if there's a prerequisite warning. |
| 1 | PREREQ\_ONLY. Run only the prerequisite. |
| 2 | CONTINUE\_ON\_PREREQ\_WARNING. During installation, ignore the prerequisite warning. |

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).