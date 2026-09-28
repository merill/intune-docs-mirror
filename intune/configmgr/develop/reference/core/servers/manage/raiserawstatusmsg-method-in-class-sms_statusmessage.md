---
layout: Conceptual
title: RaiseRawStatusMsg Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage
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
description: The RaiseRawStatusMsg Windows Management Instrumentation (WMI) class method creates a status message from an external message DLL.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4c2f50ca-e30a-adfd-0680-07a7879bd57e
document_version_independent_id: e0e7760d-9497-49ba-4f61-ed476ac54c44
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fea12245-56be-c594-5913-138bcd467e26
---

# RaiseRawStatusMsg Method - Configuration Manager | Microsoft Learn

The `RaiseRawStatusMsg` Windows Management Instrumentation (WMI) class method, in Configuration Manager, creates a status message from an external message DLL.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 RaiseRawStatusMsg(
   String ModuleName,
   UInt32 MessageType,
   UInt32 MessageID,
   UInt32 Win32Error,
   UInt32 ProcessID,
   UInt32 ThreadID,
   DateTime Time,
   UInt32 AttrIDs[],
   String AttrValues[],
   String TopLevelSiteCode
);
```

#### Parameters

`ModuleName` Data type: `String`

Qualifiers: [in]

The name of the DLL module.

`MessageType` Data type: `UInt32`

Qualifiers: [in]

The message type. Possible values are defined by the `MessageType` property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`MessageID` Data type: `UInt32`

Qualifiers: [in, Range("0-65535")]

ID of the message. See the `MessageID` property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`Win32Error` Data type: `UInt32`

Qualifiers: [in, optional]

Win32 error code associated with the status message.

`ProcessID` Data type: `UInt32`

Qualifiers: [in, optional]

ID of the process that created the message. The default value is 0.

`ThreadID` Data type: `UInt32`

Qualifiers: [in, optional]

ID of the thread that created the message. The default value is 0.

`Time` Data type: `DateTime`

Qualifiers: [in, optional]

Date and time, in Universal Coordinated Time (UTC), when the status message was created. The default value indicates current time.

`AttrIDs` Data type: `UInt32` Array

Qualifiers: [in, optional]

IDs of message attributes.

`AttrValues` Data type: `String` Array

Qualifiers: [in, optional]

Values of message attributes.

`TopLevelSiteCode` Data type: `String`

Qualifiers: [in, optional]

This property is deprecated.

## Return Values

A `UInt32` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).