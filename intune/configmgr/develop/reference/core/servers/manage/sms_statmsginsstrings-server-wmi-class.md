---
layout: Conceptual
title: SMS_StatMsgInsStrings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statmsginsstrings-server-wmi-class
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
description: Learn how to represent insertion strings in the status message using SMS_StatMsgInsStrings class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7259e759-1fd3-e573-773f-be772f0aedb9
document_version_independent_id: 5bed5540-70b7-d16f-5cae-24007ac835b8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_statmsginsstrings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_statmsginsstrings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_statmsginsstrings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 05578e7c-1584-1091-d864-8704907386bf
---

# SMS_StatMsgInsStrings Class - Configuration Manager | Microsoft Learn

The `SMS_StatMsgInsStrings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents insertion strings that are inserted into the status message.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StatMsgInsStrings : SMS_BaseClass
{
    UInt32 InsStrIndex;
     String InsStrValue;
     SInt64 RecordID;
};
```

## Methods

The `SMS_StatMsgInsStrings` class does not define any methods.

## Properties

`InsStrIndex` Data type: `UInt32`

Access type: Read

Qualifiers: [Description(""), key]

The index defining the order of the insertion strings. The index directly relates to the insertion points in the status message.

`InsStrValue` Data type: `String`

Access type: Read

Qualifiers: None

Text to insert into the insertion point.

`RecordID` Data type: `SInt64`

Access type: Read

Qualifiers: [key]

Record ID of the status message to which the insertion point belongs.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class represents insertion strings for Configuration Manager component messages and user-defined messages. The status message is represented by [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class). Your application can use the [RaiseRawStatusMsg Method in Class SMS_StatusMessage](raiserawstatusmsg-method-in-class-sms_statusmessage) to add insertion strings. To delete insertion strings, the application deletes the associated status message.

Note

Use the [SMS_StatInsStr Server WMI Class](sms_statinsstr-server-wmi-class) for a high-performance version of this class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).