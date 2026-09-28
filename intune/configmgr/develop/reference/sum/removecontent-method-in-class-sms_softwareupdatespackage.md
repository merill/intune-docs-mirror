---
layout: Conceptual
title: RemoveContent method in class SMS_SoftwareUpdatesPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage
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
description: In Configuration Manager, the RemoveContent Windows Management Instrumentation class method removes old or unnecessary content from the software updates package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4b5efe30-c25a-f210-891d-19043bf78c16
document_version_independent_id: 57d3ea1e-6a9d-6009-3fff-a94ffb02122f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e7deffe4-7fb5-b12b-2666-7a93b98e9a29
---

# RemoveContent method in class SMS_SoftwareUpdatesPackage - Configuration Manager | Microsoft Learn

The `RemoveContent` Windows Management Instrumentation (WMI) class method, in Configuration Manager, removes old or unnecessary content from the software updates package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RemoveContent(
     UInt32 ContentIDs[],
     Boolean bRefreshDPs
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: [in]

IDs of content to remove from the software updates package.

`bRefreshDPs` Data type: `Boolean`

Qualifiers: [in, optional]

`true`, by default, to replicate package content to the distribution points.

## Return Values

The method returns an exception on failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

To determine the content to remove using this method, your application should use [SMS_CIToContent Server WMI Class](sms_citocontent-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).