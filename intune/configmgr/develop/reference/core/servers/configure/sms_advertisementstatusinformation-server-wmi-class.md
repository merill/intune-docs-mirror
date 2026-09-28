---
layout: Conceptual
title: SMS_AdvertisementStatusInformation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisementstatusinformation-server-wmi-class
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
description: Learn how to represent the state and description for a software distribution or software update status message in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6dcc9097-c69b-e4b2-f651-f532971534db
document_version_independent_id: 76b8a269-c0ba-10c8-2cc8-c2f21e64dc7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_advertisementstatusinformation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_advertisementstatusinformation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_advertisementstatusinformation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 68add8a2-a323-7cd7-832b-3d6024ac97a1
---

# SMS_AdvertisementStatusInformation Class - Configuration Manager | Microsoft Learn

The `SMS_AdvertisementStatusInformation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the state and description for a software distribution or software update status message.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AdvertisementStatusInformation : SMS_BaseClass
{
      UInt32 MessageID;
      String MessageName;
      UInt32 MessageState;
      String MessageStateName;
};
```

## Methods

The `SMS_AdvertisementStatusInformation` class does not define any methods.

## Properties

`MessageID` Data type: `UInt32`

Access type: Read/write

Qualifiers: [key]

Software distribution or software update message ID.

`MessageName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Short description of the status message.

`MessageState` Data type: `UInt32`

Access type: Read/write

Qualifiers: None

Numeric category (software update states &gt;= 100, software distribution &lt; 100). For more information, see the Remarks section later in this topic.

`MessageStateName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Short description of the message state.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    The `MessageState` property can have one of the following values:

| MessageState | Type | MessageStateName |
| --- | --- | --- |
| -1 | Delivery | Accepted - No further status |
| 0 | Acceptance/Delivery | No Status |
| 1 | Acceptance | Accepted |
| 2 | Acceptance | Rejected |
| 3 | Acceptance | Expired |
| 4 | Delivery | Will Not Rerun |
| 5 | Delivery | Download in Progress |
| 6 | Delivery | Download Complete |
| 7 | Delivery | Canceled |
| 8 | Delivery | Waiting |
| 9 | Delivery | Running |
| 10 | Delivery | Retrying |
| 11 | Delivery | Failed |
| 12 | Delivery | Reboot Pending |
| 13 | Delivery | Succeeded |

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).