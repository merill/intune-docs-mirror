---
layout: Conceptual
title: CheckLockRequest Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/checklockrequest-method-in-class-sms_objectlock
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
description: The CheckLockRequest Windows Management Instrumentation (WMI) class method checks a lock request.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8f53f16c-adfa-59e7-f001-234d867cb6dd
document_version_independent_id: 412eb96b-893e-5077-9ce0-e55ee1d74c52
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/checklockrequest-method-in-class-sms_objectlock.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/checklockrequest-method-in-class-sms_objectlock
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/checklockrequest-method-in-class-sms_objectlock.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 646757d3-51b8-4672-cf22-95664fbb0e38
---

# CheckLockRequest Method - Configuration Manager | Microsoft Learn

The `CheckLockRequest` Windows Management Instrumentation (WMI) class method, in Configuration Manager, checks a lock request.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CheckLockRequest(
    string RequestID,
    uint32 Timeout,
    uint32 RequestState,
    uint32 LockState,
    string AssignedUser,
    string AssignedObjectLockContext,
    string AssignedMachine,
    string AssignedSiteCode,
    datetime AssignedTimeUTC
);
```

#### Parameters

`RequestID` Data type: `String`

Qualifiers: [in, out]

Unique identifier of the request.

`Timeout` Data type: `UInt32`

Qualifiers: [in, optional]

Seconds to wait for lock request response.

`RequestState` Data type: `UInt32`

Qualifiers: [out]

The state of the lock request. Possible values are:

| Value | Request state |
| --- | --- |
| 0 | Unknown |
| 2 | Requested |
| 3 | RequestCanceled |
| 4 | ResponseReceived |
| 10 | Granted |
| 11 | GrantedAfterTimeout |
| 12 | GrantedLockWasOrphaned |
| 20 | DeniedLockAlreadyAssigned |
| 21 | DeniedInvalidObjectVersion |
| 22 | DeniedLockNotFound |
| 23 | DeniedLockNotLocal |
| 24 | DeniedRequestTimedOut |
| 50 | Error |
| 52 | ErrorRequestNotFound |
| 53 | ErrorRequestTimedOut |

`LockState` Data type: `UInt32`

Qualifiers: [out]

Indicates the current state of the requested lock. Possible values are:

| Value | Lock state |
| --- | --- |
| 0 | Unassigned |
| 1 | Assigned |
| 2 | Requested |
| 3 | PendingAssignment |
| 4 | TimedOut |
| 5 | NotFound |

`AssignedUser` Data type: `String`

Qualifiers: [out]

Indicates the currently assigned user of the requested lock.

`AssignedObjectLockContext` Data type: `String`

Qualifiers: [out]

Indicates the unique string identifier of the requested lock.

`AssignedMachine` Data type: `String`

Qualifiers: [out]

Indicates ObjectLockContext the lock is currently assigned to.

`AssignedSiteCode` Data type: `String`

Qualifiers: [out]

Indicates the current site of the requested lock.

`AssignedTimeUTC` Data type: `DateTime`

Qualifiers: [out]

Indicates the time at which the requested lock was assigned.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).