---
layout: Conceptual
title: ExcludeAndInclude Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/excludeandinclude-method-in-class-sms_migrationentity
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
description: In Configuration Manager, the ExcludeAndInclude WMI class method marks the entities as excluded or included.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2aacf613-680c-930d-ce25-0703e05705d2
document_version_independent_id: 8e200f98-5166-49e1-1cd6-4ba79d078d2c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/excludeandinclude-method-in-class-sms_migrationentity.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/excludeandinclude-method-in-class-sms_migrationentity
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/excludeandinclude-method-in-class-sms_migrationentity.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c5f72e95-85f4-95f9-a90e-93202004ff20
---

# ExcludeAndInclude Method - Configuration Manager | Microsoft Learn

The `ExcludeAndInclude` Windows Management Instrumentation (WMI) class method, in Configuration Manager, marks the entities as excluded or included.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ExcludeAndInclude(  
     UInt32 excludeEntityList[],  
     UInt32 includeEntityList[]  
);  
```

#### Parameters

`excludeEntityList` Data type: `UInt32` Array

Qualifiers: [in]

List of entities excluded.

`includeEntityList` Data type: `UInt32` Array

Qualifiers: [in]

List of entities included.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).