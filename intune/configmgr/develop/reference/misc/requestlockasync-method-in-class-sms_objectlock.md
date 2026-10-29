---
layout: Conceptual
title: RequestLockAsync Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlockasync-method-in-class-sms_objectlock
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
description: Learn how to use the RequestLockAsync method in Configuration Manager to asynchronously acquire a lock to edit global objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fe3a6934-ab11-20be-eb6a-5a5ec2736cdb
document_version_independent_id: 0d7c4a56-741f-3e89-e413-faedffd93597
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/requestlockasync-method-in-class-sms_objectlock.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/requestlockasync-method-in-class-sms_objectlock
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/requestlockasync-method-in-class-sms_objectlock.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: eec76038-ccab-09a7-97bc-85cc5b7c32f3
---

# RequestLockAsync Method - Configuration Manager | Microsoft Learn

The `RequestLockAsync` Windows Management Instrumentation (WMI) class method, in Configuration Manager, asynchronously acquires a lock to edit global objects.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RequestLockAsync(
    string ObjectRelPath,
    boolean RequestTransfer,
    string RequestID
);
```

#### Parameters

`ObjectRelPath` Data type: `String`

Qualifiers: [in]

The path of the object for which the lock is requested.

`RequestTransfer` Data type: `Boolean`

Qualifiers: [in, optional]

If the lock is not owned by the local site, the lock request should be forwarded to the parent/child site.

`RequestID` Data type: `String`

Qualifiers: [out]

Unique identifier of the request.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).