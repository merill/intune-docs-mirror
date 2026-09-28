---
layout: Conceptual
title: CheckReferencesShareType Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/checkreferencessharetype-method-in-class-sms_tasksequencepackage
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
description: In Configuration Manager, the CheckReferencesShareType WMI class method checks all referred packages for this task sequence and returns all packages that aren't shared.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: be5f7373-129d-a023-276d-7d8431b94dbb
document_version_independent_id: bb37fa2f-4a8b-8e5f-45eb-ee6273203346
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/checkreferencessharetype-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/checkreferencessharetype-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/checkreferencessharetype-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5fc43e8d-6b75-bcca-6d4a-758b1c252fad
---

# CheckReferencesShareType Method - Configuration Manager | Microsoft Learn

The `CheckReferencesShareType` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that checks all referred packages for this task sequence and returns all packages that aren't shared.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 CheckReferencesShareType
{
    [IN]    String PackageID
    [OUT]   Boolean CanRunFromDP
    [OUT]   String PacakgeIds[]
    [OUT]   String PackageNames[]
};
```

## Parameters

`PackageID` Data type: `String`

Qualifiers: [id("0"), in]

Task sequence package identifier.

`CanRunFromDP` Data type: `Boolean`

Qualifiers: [id("1"), out]

`true` if the package can be run from the distribution point.

`PacakgeIds` Data type: `String Array`

Qualifiers: [id("2"), out]

Package identifiers for all referred packages for this task sequence that aren't shared.

Note

The incorrect spelling of the variable "PacakgeIds" is hardcoded in WMI.

`PackageNames` Data type: `String Array`

Qualifiers: [id("3"), out]

Package names for all referred packages for this task sequence that aren't shared.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).