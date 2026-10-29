---
layout: Conceptual
title: Stop Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/stop-method-in-class-sms_migrationjob
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
description: Learn how to stop the migration job in Configuration Manager using the Stop class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c617aacb-ef46-72d9-c658-67e239ee42d8
document_version_independent_id: a5477636-d8c3-c779-094c-22ccd28be485
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/stop-method-in-class-sms_migrationjob.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/stop-method-in-class-sms_migrationjob
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/stop-method-in-class-sms_migrationjob.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 596f6bdc-df62-4604-7409-1053f493a83d
---

# Stop Method - Configuration Manager | Microsoft Learn

The `Stop` Windows Management Instrumentation (WMI) class method, in Configuration Manager, stops the migration job.

Important

This requires the Manage Migration Job right.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 Stop();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).