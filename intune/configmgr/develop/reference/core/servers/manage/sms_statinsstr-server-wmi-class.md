---
layout: Conceptual
title: SMS_StatInsStr Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statinsstr-server-wmi-class
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
description: Learn how to use the SMS_StatInsStr Class to represent a high-performance version of SMS_StatMsgInsStrings Server WMI class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3e9ae826-6af7-35cd-14b5-bc4f7f1085d9
document_version_independent_id: 0c203506-9505-4b5b-7ff9-526032f592c0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_statinsstr-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_statinsstr-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_statinsstr-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: caf7660f-c59e-51c0-d8e9-79dbfa2a3202
---

# SMS_StatInsStr Class - Configuration Manager | Microsoft Learn

The `SMS_StatInsStr` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a high-performance version of [SMS_StatMsgInsStrings Server WMI Class](sms_statmsginsstrings-server-wmi-class).

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StatInsStr : SMS_BaseClass
{
      UInt32 InsStrIndex;
      String InsStrValue;
      SInt64 RecordID;
};
```

## Methods

The `SMS_StatInsStr` class does not define any methods.

## Properties

`InsStrIndex` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The index defining the order of the insertion strings. The index directly relates to the insertion points in the status message.

`InsStrValue` Data type: `String`

Access type: Read

Qualifiers: none

Text to insert into the insertion point.

`RecordID` Data type: `SInt64`

Access type: Read

Qualifiers: none

Record ID of the status message to which the insertion point belongs.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class represents insertion strings for Configuration Manager component messages and user-defined messages. The status message is represented by [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class). Your application can use the [RaiseRawStatusMsg Method in Class SMS_StatusMessage](raiserawstatusmsg-method-in-class-sms_statusmessage) to add insertion strings. To delete insertion strings, the application deletes the associated status message.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).