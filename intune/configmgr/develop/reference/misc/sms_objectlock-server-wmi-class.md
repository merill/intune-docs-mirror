---
layout: Conceptual
title: SMS_ObjectLock Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_objectlock-server-wmi-class
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
description: The SMS_ObjectLock abstract WMI class represents methods for locking and unlocking global objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ac6ac09c-e9c8-38a9-7d97-c6e97012383d
document_version_independent_id: 1d16b9f9-ec35-ec56-038c-7214669a646c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_objectlock-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_objectlock-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_objectlock-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e574d7dc-bc44-82be-70a7-d238dd5c0353
---

# SMS_ObjectLock Class - Configuration Manager | Microsoft Learn

The `SMS_ObjectLock` abstract Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents methods for locking and unlocking global objects.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectLock : SMS_BaseClass
{
};
```

## Methods

The following table shows the methods in `SMS_ObjectLock`.

| Method | Description |
| --- | --- |
| [CancelLockRequest Method in Class SMS_ObjectLock](cancellockrequest-method-in-class-sms_objectlock) | Cancels a lock request. |
| [CancelLockRequests Method in Class SMS_ObjectLock](cancellockrequests-method-in-class-sms_objectlock) | Cancels multiple lock requests. |
| [CheckLockRequest Method in Class SMS_ObjectLock](checklockrequest-method-in-class-sms_objectlock) | Checks a lock request. |
| [CheckLockRequests Method in Class SMS_ObjectLock](checklockrequests-method-in-class-sms_objectlock) | Checks multiple lock requests. |
| [GetLockInformation Method in Class SMS_ObjectLock](getlockinformation-method-in-class-sms_objectlock) | Gets current lock information. |
| [ReleaseAllLocks Method in Class SMS_ObjectLock](releasealllocks-method-in-class-sms_objectlock) | Releases all locks for a session. |
| [ReleaseLock Method in Class SMS_ObjectLock](releaselock-method-in-class-sms_objectlock) | Releases a lock to global object. |
| [ReleaseLocks Method in Class SMS_ObjectLock](releaselocks-method-in-class-sms_objectlock) | Releases locks to multiple global objects. |
| [RequestLock Method in Class SMS_ObjectLock](requestlock-method-in-class-sms_objectlock) | Synchronously acquires a lock to edit global object. |
| [RequestLockAsync Method in Class SMS_ObjectLock](requestlockasync-method-in-class-sms_objectlock) | Asynchronously acquires a lock to edit global objects. |
| [RequestLocks Method in Class SMS_ObjectLock](requestlocks-method-in-class-sms_objectlock) | Synchronously acquires a lock to edit a global object. |
| [RequestLocksAsync Method in Class SMS_ObjectLock](requestlocksasync-method-in-class-sms_objectlock) | Asynchronously acquires locks to edit multiple global objects. |

## Properties

None.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).