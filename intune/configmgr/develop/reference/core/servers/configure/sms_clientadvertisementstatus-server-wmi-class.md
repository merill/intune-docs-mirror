---
layout: Conceptual
title: SMS_ClientAdvertisementStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_clientadvertisementstatus-server-wmi-class
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
description: The SMS_ClientAdvertisementStatus WMI class is an SMS Provider server class, in Configuration Manager, that records the last status message for every client and advertisement.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 81b0b023-3ae2-e3a5-c4e4-7e4f1493de0b
document_version_independent_id: 12130e8a-ea78-d926-f265-92e782740c13
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_clientadvertisementstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_clientadvertisementstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_clientadvertisementstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 64bf748f-f839-333b-3878-23dff9bf3272
---

# SMS_ClientAdvertisementStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ClientAdvertisementStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that records the last status message for every client and advertisement.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientAdvertisementStatus : SMS_BaseClass
{
      String AdvertisementID;
      UInt32 LastAcceptanceMessageID;
      String LastAcceptanceMessageIDName;
      UInt32 LastAcceptanceMessageIDSeverity;
      UInt32 LastAcceptanceState;
      String LastAcceptanceStateName;
      DateTime LastAcceptanceStatusTime;
      String LastExecutionContext;
      String LastExecutionResult;
      UInt32 LastState;
      String LastStateName;
      UInt32 LastStatusMessageID;
      String LastStatusMessageIDName;
      UInt32 LastStatusMessageIDSeverity;
      DateTime LastStatusTime;
      UInt32 ResourceID;
};
```

## Methods

The `SMS_ClientAdvertisementStatus` class does not define any methods.

## Properties

`AdvertisementID` Data type: `String`

Access type: Read Only

Qualifiers: [key]

ID of the advertisement.

`LastAcceptanceMessageID` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Last acceptance status message ID.

`LastAcceptanceMessageIDName` Data type: `String`

Access type: Read Only

Qualifiers: None

Short description of the last acceptance status message.

`LastAcceptanceMessageIDSeverity` Data type: `UInt32`

Access type: Read Only

Qualifiers: [enumeration]

The severity of the last acceptance status message. Possible values are:

| Value | Status message severity |
| --- | --- |
| 0x40000000 | Error(3221225472) |
| 0x80000000 | Warning(2147483648) |
| 0xC0000000 | Informational(1073741824) |

`LastAcceptanceState` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Numeric category of the last acceptance status message.

`LastAcceptanceStateName` Data type: `String`

Access type: Read Only

Qualifiers: None

Short description of the acceptance category.

`LastAcceptanceStatusTime` Data type: `DateTime`

Access type: Read Only

Qualifiers: None

Date and time, in Universal Coordinated Time (UTC), when the last acceptance message was generated.

`LastExecutionContext` Data type: `String`

Access type: Read Only

Qualifiers: None

User context (account) under which the program ran.

`LastExecutionResult` Data type: `String`

Access type: Read Only

Qualifiers: None

Last string returned by a status Management Information Format (MIF) file (messages 10007 and 10009) or an error return code (10006).

`LastState` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Numeric category of the last delivery status message.

`LastStateName` Data type: `String`

Access type: Read Only

Qualifiers: None

Short description of the delivery category.

`LastStatusMessageID` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Last delivery status message ID.

`LastStatusMessageIDName` Data type: `String`

Access type: Read Only

Qualifiers: None

Short description of the last delivery status message.

`LastStatusMessageIDSeverity` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

[enumeration]

The severity of the last delivery status message. Possible values are listed for `LastAcceptanceMessageIDSeverity`.

`LastStatusTime` Data type: `DateTime`

Access type: Read Only

Qualifiers: None

Date and time, in Universal Coordinated Time (UTC), when the last delivery message was generated.

`ResourceID` Data type: `UInt32`

Access type: Read Only

Qualifiers: [key]

ID of the resource for the client.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Using this class is the primary way to determine advertisement status. Even if a client is no longer in the collection targeted by an advertisement, an instance still appears in this class. It records the last status message for every advertisement for each client.

    Advertisement status is divided into two stages, Acceptance and Delivery, which are recorded separately. Acceptance is whether the client has received the advertisement and whether the client decides that the advertisement applies to it. Delivery is the status of everything that comes after; that is, the actual download and execution of the advertisement. Advertisement status messages have been categorized into several groups that indicate similar status for the advertisement.

    For more information about categories see [SMS_AdvertisementStatusInformation Server WMI Class](sms_advertisementstatusinformation-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).