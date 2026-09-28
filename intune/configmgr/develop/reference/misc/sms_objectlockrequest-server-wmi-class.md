---
layout: Conceptual
title: SMS_ObjectLockRequest Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_objectlockrequest-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents object lock request information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b95779c6-1e24-f873-7822-6c58ecb052a9
document_version_independent_id: a1dcee93-5815-db38-af2f-f6195f6424e4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_objectlockrequest-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_objectlockrequest-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_objectlockrequest-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8b8fb225-1075-5efa-b774-02eaec0775dc
---

# SMS_ObjectLockRequest Class - Configuration Manager | Microsoft Learn

The `SMS_ObjectLockRequest` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents object lock request information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectLockRequest :
{
    String AssignedMachine;
    String AssignedObjectLockContext;
    String AssignedSiteCode;
    DateTime AssignedTimeUTC;
    String AssignedUser;
    UInt32 LockState;
    String ObjectRelPath;
    String RequestID;
    UInt32 RequestState;
};
```

## Methods

The `SMS_ObjectLockRequest` class does not define any methods.

## Properties

`AssignedMachine` Data type: `String`

Access type: Read/Write

Qualifiers: none

Indicates the currently assigned computer of the requested lock.

`AssignedObjectLockContext` Data type: `String`

Access type: Read/Write

Qualifiers: none

Indicates ObjectLockContext the lock is currently assigned to.

`AssignedSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Indicates the current site of the requested lock.

`AssignedTimeUTC` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Indicates the time at which the requested lock was assigned.

`AssignedUser` Data type: `String`

Access type: Read/Write

Qualifiers: none

Indicates the currently assigned user of the requested lock.

`LockState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the current state of the requested lock. Possible values are:

| Value | Lock state |
| --- | --- |
| 0 | Unassigned |
| 1 | Assigned |
| 2 | Requested |
| 3 | PendingAssignment |
| 4 | TimedOut |
| 5 | NotFound |

`ObjectRelPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

The path of the object for which the lock is requested.

`RequestID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier of the request.

`RequestState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

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

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).