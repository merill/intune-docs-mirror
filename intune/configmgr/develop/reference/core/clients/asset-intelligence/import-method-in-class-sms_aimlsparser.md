---
layout: Conceptual
title: Import Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/import-method-in-class-sms_aimlsparser
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
description: A Windows Management Instrumentation class method that imports the MLS statement as specified by the MLSFilepath parameter into the Configuration Manager database.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1af9154f-bb2f-20e0-bb6f-408b8802f71b
document_version_independent_id: a94784b4-20b9-9299-6f54-a8d4e31d10aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/import-method-in-class-sms_aimlsparser.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/import-method-in-class-sms_aimlsparser
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/import-method-in-class-sms_aimlsparser.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 22fa8665-6514-4578-0de7-75ac78c2ef6f
---

# Import Method - Configuration Manager | Microsoft Learn

The `Import` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports the MLS statement as specified by the `MLSFilepath` parameter (in UNC format) into the Configuration Manager database.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 Import(
     String MLSFilepath,
     UInt32 Flags
);
```

#### Parameters

`MLSFilepath` Data type: `String`

Qualifiers: [in]

The UNC path of the .csv file to be imported.

`Flags` Data type: `UInt32`

Qualifiers: [in]

Specifies the type of data the .csv file contains, specified by the `MLSFilepath` property.

| Value | Description |
| --- | --- |
| 0 | Microsoft licenses. |
| Non 0 | Any non-Microsoft licenses. |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).