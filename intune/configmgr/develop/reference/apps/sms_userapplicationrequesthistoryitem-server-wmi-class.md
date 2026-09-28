---
layout: Conceptual
title: SMS_UserApplicationRequestHistoryItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_userapplicationrequesthistoryitem-server-wmi-class
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
description: Learn how to represent an update to an instance of SMS_UserApplicationRequest using SMS_UserApplicationRequestHistoryItem class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2d0ea1d0-b39f-77a2-e270-539cf31bd511
document_version_independent_id: dc5069eb-c8c1-55ee-85e9-d261de9f1245
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_userapplicationrequesthistoryitem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_userapplicationrequesthistoryitem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_userapplicationrequesthistoryitem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c9544af3-a720-f6c6-5d18-a6e54576f67b
---

# SMS_UserApplicationRequestHistoryItem Class - Configuration Manager | Microsoft Learn

The `SMS_UserApplicationRequestHistoryItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an update to an instance of `SMS_UserApplicationRequest`.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UserApplicationRequestHistoryItem :
{
    String Comments;
    String ModifiedBy;
    DateTime ModifiedDate;
    UInt32 State;
};
```

## Methods

The `SMS_UserApplicationRequestHistoryItem` class does not define any methods.

## Properties

`Comments` Data type: `String`

Access type: Read/Write

Qualifiers: none

Comments entered to explain why the change occurred. These could be user's comment explaining why they are requesting the application or approver comments explaining why the application was approved or denied.

`ModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

The user who made the change to the request.

`ModifiedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The date when the change to the request was made.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The state of the request after the change was made. Possible values are:

| Value | State |
| --- | --- |
| 1 | Requested |
| 2 | Canceled |
| 3 | Denied |
| 4 | Approved |

## Remarks

## Requirements

Each time a request is updated, an instance of this class is created to track the history of the request.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).