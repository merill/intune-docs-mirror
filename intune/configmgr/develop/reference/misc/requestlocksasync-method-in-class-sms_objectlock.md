---
layout: Conceptual
title: RequestLocksAsync Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlocksasync-method-in-class-sms_objectlock
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
description: Learn how to asynchronously acquire locks to edit multiple global objects using RequestLocksAsync class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dd04dc1e-4d02-e09e-3402-454fe66423e3
document_version_independent_id: d171b2c9-ac4f-0b99-ed2c-9e7bd66c715b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/requestlocksasync-method-in-class-sms_objectlock.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/requestlocksasync-method-in-class-sms_objectlock
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/requestlocksasync-method-in-class-sms_objectlock.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 661b2430-5496-cd57-a7bb-82db36007405
---

# RequestLocksAsync Method - Configuration Manager | Microsoft Learn

The `RequestLocksAsync` Windows Management Instrumentation (WMI) class method, in Configuration Manager, asynchronously acquires locks to edit multiple global objects.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RequestLocksAsync(
    string ObjectRelPath[],
    boolean RequestTransfer,
    SMS_ObjectLockRequest ObjectLockRequests[]
);
```

#### Parameters

`ObjectRelPath` Data type: `String` Array

Qualifiers: [in]

The paths of the objects for which the locks are requested. `RequestTransfer` Data type: `Boolean`

Qualifiers: [in, optional]

If the lock is not owned by the local site, the lock request should be forwarded to the parent/child site.

`ObjectLockRequests` Data type: `SMS_ObjectLockRequest` Array

Qualifiers: [out]

A WMI class that represents object lock request information.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).