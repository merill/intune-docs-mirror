---
layout: Conceptual
title: Release a Lock on a SEDO-Enabled Object - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-release-a-lock-on-a-sedo-enabled-object
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: Learn about how to release a locked SEDO-enabled object using its object path by creating a ReleaseLock method.
locale: en-us
document_id: 1aaa0db3-73af-0a70-4561-721464a13c8d
document_version_independent_id: 7c05f2c4-366a-ae56-21f2-2d76f7b61041
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-release-a-lock-on-a-sedo-enabled-object.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-release-a-lock-on-a-sedo-enabled-object
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-release-a-lock-on-a-sedo-enabled-object.md
cmProducts: []
platformId: 2ebfa8f1-af0f-dd2c-8959-3173091e132a
---

# Release a Lock on a SEDO-Enabled Object - Configuration Manager | Microsoft Learn

### To Release an Explicit Lock on a SEDO-enabled Object

1. Create an instance of the `SMS_ObjectLock` WMI class
2. Get the method parameters object for the `ReleaseLock` method.
3. Assign the object path of the object you wish to unlock to the `ObjectRelPath` property.
4. Create an `InvokeMethodOptions` object instance. On the Context property, add a name/value pair. The name must be "MachineName" and the value must be name of the computer releasing the lock. For more information, see [How to Acquire a Lock on a SEDO-Enabled Object](how-to-acquire-a-lock-on-a-sedo-enabled-object)
5. Call **InvokeMethod** on the `SMS_ObjectLock` instance.
6. **InvokeMethod** will return a `SMS_ObjectLockRequest` instance. Check the `RequestState` and `LockState` properties to get more information on the success or failure of the request.

## Example

The following example releases a lock on a `SMS_ConfigurationItem` object instance.

```
class Program
{
    static void Main(string[] args)
    {
        ManagementScope scope = new ManagementScope(@"\siteservername\root\sms\site_ABC");
        ReleaseLock(scope);
    }

    public static void ReleaseLock(ManagementScope scope)
    {
        ManagementPath path = new ManagementPath("SMS_ObjectLock");
        ManagementClass objectLock = new ManagementClass(scope, path, null);

        ManagementBaseObject inParams = objectLock.GetMethodParameters("ReleaseLock");
        inParams["ObjectRelPath"] = "SMS_ConfigurationItem.CI_ID=30";

        InvokeMethodOptions options = new InvokeMethodOptions();
        options.Context.Add("MachineName", "RequestingComputer");

        ManagementBaseObject result = objectLock.InvokeMethod("ReleaseLock", inParams, options);

    }
}

```

The **SMS\_ObjectLockRequest** object contains the following properties:

| Property | Description |
| --- | --- |
| RequestID | Unique identifier of the request. |
| ObjectRelPath | The path of the object for which the lock is requested. |
| RequestState | Indicates the success or failure of the request. |
| LockState | Indicates the current state of the requested lock. |
| AssignedUser | Indicates the currently assigned user of the requested lock. |
| AssignedObjectLockContext | Indicates ObjectLockContext the lock is currently assigned to. |
| AssignedMachine | Indicates the currently assigned computer of the requested lock. |
| AssignedSiteCode | Indicates the current site of the requested lock. |
| AssignedTimeUTC | Indicates the time at which the requested lock was assigned. |

RequestState The table below displays the possible request state values. Request states Granted, GrantedAfterTimeout and GrantedLockWasOrphaned indicate a successful request and the user can then make and save modifications to the object. All other requests indicate error.

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

LockState The table below displays the possible lock state values.

| LockStateID | LockStateName |
| --- | --- |
| 0 | Unassigned |
| 1 | Assigned |
| 2 | Requested |
| 3 | PendingAssignment |
| 4 | TimedOut |
| 5 | NotFound |

## Compiling the Code

The C# example requires:

### Namespaces

System

System.Management

### Assembly

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).