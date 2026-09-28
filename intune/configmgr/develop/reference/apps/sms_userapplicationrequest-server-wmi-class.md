---
layout: Conceptual
title: SMS_UserApplicationRequest Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_userapplicationrequest-server-wmi-class
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
description: In Configuration Manager, the SMS_UserApplicationRequest WMI class is an SMS Provider server class that represents a user's application request.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6f8d73a8-71cb-e5b5-09cd-a6738beb2dd5
document_version_independent_id: f6bd6957-0ae0-1b37-33ec-65404cf8e93c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_userapplicationrequest-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_userapplicationrequest-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_userapplicationrequest-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 851ca0d3-1bdf-884a-b194-37c2164e704a
---

# SMS_UserApplicationRequest Class - Configuration Manager | Microsoft Learn

The `SMS_UserApplicationRequest` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a user's application request.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UserApplicationRequest :
{
    String Application;
    String CI_UniqueID;
    String Comments;
    UInt32 CurrentState;
    String LastModifiedBy;
    DateTime LastModifiedDate;
    String ModelName;
    String RequestGuid;
    SMS_UserApplicationRequestHistoryItem RequestHistory[];
    String User;
    String UserSid;
};
```

## Methods

The following table lists the methods in the `SMS_UserApplicationRequest` class.

| Method | Description |
| --- | --- |
| [Approve Method in Class SMS_UserApplicationRequest](approve-method-in-class-sms_userapplicationrequest) | Approves a user application request. |
| [Deny Method in Class SMS_UserApplicationRequest](deny-method-in-class-sms_userapplicationrequest) | Denies a user application request. |

## Properties

`Application` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the application.

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique ID of the configuration item. This ID is unique across sites.

`Comments` Data type: `String`

Access type: Read/Write

Qualifiers: none

Last set of comments for the request.

`CurrentState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Current state of the application request. Possible values are:

| Value | Current state |
| --- | --- |
| 1 | Requested |
| 2 | Canceled |
| 3 | Denied |
| 4 | Approved |

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

User who last modified the request.

`LastModifiedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date and time for the last modification of this request.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model name of the requested application.

`RequestGuid` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique GUID for the request.

`RequestHistory` Data type: `SMS_UserApplicationRequestHistoryItem Array`

Access type: Read/Write

Qualifiers: [lazy]

History of the request, one entry per update that was done.

`User` Data type: `String`

Access type: Read/Write

Qualifiers: none

User that requested the application.

`UserSid` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Security identifier of the user that requested the application.

## Remarks

## Requirements

A user application request is unique for a given user and application.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).