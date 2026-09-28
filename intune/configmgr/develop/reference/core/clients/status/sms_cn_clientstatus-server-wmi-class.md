---
layout: Conceptual
title: SMS_CN_ClientStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_cn_clientstatus-server-wmi-class
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
description: The SMS_CN_ClientStatus Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents client notification of agent status.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b28c1ba5-80f5-bc47-b5f0-d31db5065af4
document_version_independent_id: e5e277e4-c03b-004d-2df2-ac9edc0333bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/status/sms_cn_clientstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/status/sms_cn_clientstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/status/sms_cn_clientstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 49acd847-f9e0-9d75-d5c4-6899455d0760
---

# SMS_CN_ClientStatus Class - Configuration Manager | Microsoft Learn

The `SMS_CN_ClientStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents client notification of agent status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CN_ClientStatus : SMS_BaseClass
{
    UInt32 ChannelType;
    DateTime LastStatusTime;
    UInt32 OnlineStatus;
    UInt32 ResourceID;
    UInt32 ServerID;
};
```

## Methods

The following table lists the methods in the `SMS_CN_ClientStatus` class.

| Method | Description |
| --- | --- |
| [GetOnlineCount Method in Class SMS_CN_ClientStatus](getonlinecount-method-in-class-sms_cn_clientstatus) | Gets an online count of the selected clients of the target collection. |

## Properties

`ChannelType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Channel type. Possible values are:

| Value | Channel type |
| --- | --- |
| 0 | TCP |
| 1 | HTTP |

`LastStatusTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last online time.

`OnlineStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Online status. Possible values are:

| Value | Online status |
| --- | --- |
| 0 | Offline |
| 1 | Online |

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Client resource identifier.

`ServerID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Client notification server identifier.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).