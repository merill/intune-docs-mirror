---
layout: Conceptual
title: SMS_StateInformation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_stateinformation-server-wmi-class
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
description: The SMS_StateInformation WMI class provides information about a state message.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 86e8b320-177a-0b01-74f0-3262970cbb46
document_version_independent_id: d0420969-a68a-9b2a-e98d-64edf8095d94
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_stateinformation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_stateinformation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_stateinformation-server-wmi-class.md
cmProducts: []
platformId: 50aba2ce-ca02-d7dc-58f8-e62646f3a850
---

# SMS_StateInformation Class - Configuration Manager | Microsoft Learn

The `SMS_StateInformation` WMI class is an SMS Provider server class, in Configuration Manager, that provides information about a state message.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StateInformation : SMS_BaseClass
{
      String StateDescription;
      UInt32 StateID;
      String StateName;
      UInt32 TopicType;
};
```

## Methods

The `SMS_StateInformation` class does not define any methods.

## Properties

`StateDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the state.

`StateID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the state.

`StateName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the state.

`TopicType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

State message topic type. Possible values are:

| Value | Topic type |
| --- | --- |
| 500 | Software update detection |
| 501 | Software update scan status |
| 403 | Settings management scan status |
| 401 | Settings Management compliance |
| 402 | Software updates installation |
| 300 | Software updates or desired configuration management assignment compliance |
| 301 | Software updates assignment enforcement (installation) |
| 302 | Software updates or desired configuration management assignment evaluation |
| 100 | State migration (server only) |
| 600 | PXE (server only) |
| 700 | State system resync (server only) |
| 701 | State system heartbeat (server only) |
| 800 | Client deployment FSP |
| 801 | Device client deployment FSP |
| 900 | Branch distribution point status |
| 502 | WSUS synch status |
| 1000,1001 | Client health state (FSP) |
| 1002,1003,1004 | Device client health state (FSP) |
| 1100 | Client mode readiness state |
| 702 | ClientKeyData updates (server only) |
| 1500, 1501 | CAL tracking (user) |
| 1502, 1503 | CAL tracking (computer) |

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class allows you to access information about a Configuration Manager state message. These messages are sent by clients to notify of important changes of state. Each message provides a snapshot of the state of a process at a specific time. These messages can be helpful when troubleshooting or verifying that processes are working correctly.

    State messages are used with software updates, desired configuration management, client deployment, and client communication. Generally you will use state messages only through reports and client logs.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).