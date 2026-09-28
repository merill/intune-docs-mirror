---
layout: Conceptual
title: CleanupHierarchyData Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/cleanuphierarchydata-method-in-class-sms_migrationsitemapping
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
description: The CleanupHierarchyData Windows Management Instrumentation (WMI) class method cleans up hierarchy data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9130307f-0032-f7e3-8701-71cc60720563
document_version_independent_id: 82a5c038-1b83-0f73-7c72-6f462b279cd0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/cleanuphierarchydata-method-in-class-sms_migrationsitemapping.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/cleanuphierarchydata-method-in-class-sms_migrationsitemapping
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/cleanuphierarchydata-method-in-class-sms_migrationsitemapping.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: de05efde-5294-3131-abac-93b3709be288
---

# CleanupHierarchyData Method - Configuration Manager | Microsoft Learn

The `CleanupHierarchyData` Windows Management Instrumentation (WMI) class method, in Configuration Manager, cleans up hierarchy data.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CleanupHierarchyData(  
     UInt32 siteID   
);  
```

#### Parameters

`siteID` Data type: `UInt32` Array

Qualifiers: [in]

Site ID of the Configuration Manager site.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).