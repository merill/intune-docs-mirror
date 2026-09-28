---
layout: Conceptual
title: ResolvePendingRegistrationRecord Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/resolvependingregistrationrecord-method-in-class-sms_pendingregistrationrecord
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
description: The ResolvePendingRegistrationRecord Windows Management Instrumentation (WMI) class method resolves any conflicts for the pending registration records.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f9d827fc-2546-55ed-2816-49d6501e617b
document_version_independent_id: c911abd9-a913-322c-3dc9-7f712de69cd6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/resolvependingregistrationrecord-method-in-class-sms_pendingregistrationrecord.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/resolvependingregistrationrecord-method-in-class-sms_pendingregistrationrecord
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/resolvependingregistrationrecord-method-in-class-sms_pendingregistrationrecord.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e183f489-6db8-a28e-5eb3-f8a8e64854a3
---

# ResolvePendingRegistrationRecord Method - Configuration Manager | Microsoft Learn

The `ResolvePendingRegistrationRecord` Windows Management Instrumentation (WMI) class method, in Configuration Manager, resolves any conflicts for the pending registration records.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 ResolvePendingRegistrationRecord(
     string SMSID,
     uint32 Action
);
```

#### Parameters

`SMSID` Data type: `String`

Qualifiers: [in]

Pending registration record id to use.

`Action` Data type: `UInt32`

Qualifiers: [in]

Action to execute on the pending registration record. Possible values are:

| Value | Description |
| --- | --- |
| 1 | Merge: Allows the record to take over the existing conflicting record. |
| 2 | New: Creates a new record for the `SMSID` resource. This resource is then issued a new `SMSID` value. |
| 3 | Reject: Creates a new record for the `SMSID` resource. This resource is then issued a new `SMSID` value, but is restricted from communicating with the Configuration Manager site. |

## Return Values

An `SInt32`data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).