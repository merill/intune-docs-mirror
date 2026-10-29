---
layout: Conceptual
title: RequestLock Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlock-method-in-class-sms_objectlock
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
description: Learn how to use the RequestLock method in Configuration Manager to synchronously acquire a lock to edit a global object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bf5a4ef0-da3b-609a-6220-73c0dfa6d7c5
document_version_independent_id: 28e124dc-37b7-8826-71b9-5d0490340be0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/requestlock-method-in-class-sms_objectlock.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/requestlock-method-in-class-sms_objectlock
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/requestlock-method-in-class-sms_objectlock.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 8e180981-0708-2bc9-accc-99262ede45ca
---

# RequestLock Method - Configuration Manager | Microsoft Learn

The `RequestLock` Windows Management Instrumentation (WMI) class, in Configuration Manager, synchronously acquires a lock to edit a global object.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RequestLock(
    string ObjectRelPath,
    boolean RequestTransfer,
    string RequestID,
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

`ObjectRelPath` Data type: `String`

Qualifiers: [in]

The path of the object for which the lock is requested.

`RequestTransfer` Data type: `Boolean`

Qualifiers: [in, optional]

If the lock is not owned by the local site, the lock request should be forwarded to the parent/child site.

`RequestID` Data type: `String`

Qualifiers: [out]

Unique identifier of the request.

`RequestState` Data type: `UInt32`

Qualifiers: [out]

Request state values. The request states `Granted`, `GrantedAfterTimeout` and `GrantedLockWasOrphaned` indicate a successful request and the user can then make and save modifications to the object. All other requests indicate an error.

| RequestStateID | RequestStateName |
| --- | --- |
| 0 | Unknown |
| 2 | Requested |
| 3 | RequestedCanceled |
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

Indicates ObjectLockContext the lock is currently assigned to.

`AssignedMachine` Data type: `String`

Qualifiers: [out]

Indicates the currently assigned computer of the requested lock.

`AssignedSiteCode` Data type: `String`

Qualifiers: [out]

Indicates the current site of the requested lock.

`AssignedTimeUTC` Data type: `DateTime`

Qualifiers: [out]

Indicates the current site of the requested lock.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).