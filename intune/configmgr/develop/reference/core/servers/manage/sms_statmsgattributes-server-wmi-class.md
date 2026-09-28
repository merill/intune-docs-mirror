---
layout: Conceptual
title: SMS_StatMsgAttributes Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgattributes-server-wmi-class
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
description: Learn how the SMS_StatMsgAttributes class is an SMS Provider server class that represents optional data associated with a status message.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2cd3731b-5e72-db95-12c6-0332a61c5930
document_version_independent_id: 6a26ea3f-d26e-b072-d12e-892682d8aa95
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgattributes-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_statmsgattributes-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_statmsgattributes-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 7981ffa4-dff0-254a-2f59-b5af79d9cf07
---

# SMS_StatMsgAttributes Class - Configuration Manager | Microsoft Learn

The `SMS_StatMsgAttributes` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents optional data associated with a status message.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StatMsgAttributes : SMS_BaseClass
{
      UInt32 AttributeID;
      DateTime AttributeTime;
      String AttributeValue;
      SInt64 RecordID;
};
```

## Methods

The `SMS_StatMsgAttributes` class does not define any methods.

## Properties

`AttributeID` Data type: `UInt32`

Access type: Read

Qualifiers:

[key]

Type of attribute that is defined by the `AttributeValue` property. Possible values are:

| Value | Attribute ID |
| --- | --- |
| 400 | Package ID |
| 401 | Advertisement ID |
| 402 | Collection ID |
| 403 | User Name |
| 404 | Distribution Point |
| 405 | Policy ID |
| 406 | Policy Assignment ID |
| 407 | Software Metering Rule ID |
| 408 | Client SMS Unique ID |
| 409 | Site Code |
| 410 | Package Version |
| 411 | Time Key |
| 412 | Unique Update ID |
| 413 | Product ID |
| 414 | CI Assignment ID |
| 415 | Object ID |
| 416 | Object Type |
| 419 | UpdateSourceUniqueID |
| 420 | Collection Extended Properties ID |
| 421 | Wake On LAN Object Type |
| 422 | Wake On LAN Batch ID |
| 423 | Machine Extended Properties ID |
| 424 | Wake On LAN Number of Requests |
| 425 | Unknown Machine |
| 426 | MAC Address |
| 427 | SMBIOS ID |
| 428 | Application ID |
| 429 | Application Version |

`AttributeTime` Data type: `DateTime`

Access type: Read

Qualifiers: [key]

Date and time, in Universal Coordinated Time (UTC), when the message was generated.

`AttributeValue` Data type: `String`

Access type: Read

Qualifiers: [key]

Attribute value having content that is determined by the `AttributeID` property.

`RecordID` Data type: `SInt64`

Access type: Read

Qualifiers: None

Record ID of the status message with which the attribute is associated.

## Remarks

Class qualifiers for this class include:

- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Use this class to associate specific information with a message. The attribute data is not displayed in the message text. Typically, the attribute values are used to query for status messages that reference a particular object. For example, your application can query for the attribute that retrieves all the messages associated with a particular Configuration Manager package.

    Each attribute is stored as an instance of this class. Your application can use the raise status message methods to add attribute values. To delete attribute values, the application deletes the associated status message.

Note

Use the [SMS_StatAttr Server WMI Class](sms_statattr-server-wmi-class) for a high-performance version of this class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).