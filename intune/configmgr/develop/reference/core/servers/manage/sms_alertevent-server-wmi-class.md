---
layout: Conceptual
title: SMS_AlertEvent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_alertevent-server-wmi-class
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
description: An SMS Provider server class that represents the event data for an alert.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a67110b5-7c25-e5c3-6a63-7e1de7c936fb
document_version_independent_id: 5edf038f-4995-f4c1-b620-e370e970f2ca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_alertevent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_alertevent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_alertevent-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e17b6966-dfc1-22dc-0b07-79f8e6bfe1e0
---

# SMS_AlertEvent Class - Configuration Manager | Microsoft Learn

The `SMS_AlertEvent` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents the event data for an alert.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AlertEvent : SMS_BaseClass
{
    UInt32 AlertID;
    DateTime DateClosed;
    String EventData;
    UInt32 EventID;
    String EventInstanceID;
    UInt64 EventResourceID;
    DateTime EventTime;
    Boolean IsClosed;
    String SiteCode;
};
```

## Methods

The `SMS_AlertEvent` class doesn't define any methods.

## Properties

`AlertID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier of the alert.

`DateClosed` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date on which the event was closed.

`EventData` Data type: `String`

Access type: Read/Write

Qualifiers: none

Additional data about the event in XML format.

`EventID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the event.

`EventInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifies the source of the alert.

`EventResourceID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

Resource identifier of an associated computer for computer based events. Another identifier for noncomputer based alerts.

`EventTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time the alert was raised.

`IsClosed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true`, if this event has been closed.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Site code of the site at which the event was raised.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).