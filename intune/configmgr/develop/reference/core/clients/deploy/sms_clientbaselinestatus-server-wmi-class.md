---
layout: Conceptual
title: SMS_ClientBaselineStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselinestatus-server-wmi-class
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
description: The SMS_ClientBaselineStatus WMI class is an SMS Provider server class, in Configuration Manager, that represents a client deployment baseline status.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5adc70c2-3002-e58b-3287-1bb572760380
document_version_independent_id: 6bdf55a0-c885-514b-cd33-b33f9e4ed7bd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselinestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientbaselinestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselinestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 18ad8226-798f-8c75-8989-948c8526671c
---

# SMS_ClientBaselineStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ClientBaselineStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a client deployment baseline status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientBaselineStatus: SMS_BaseClass
{
    UInt32 BaselineType;
    String InstalledClientVersion;
    UInt32 LastErrorCode;
    UInt32 ResourceID;
    String  SMSID;
    UInt32 Status;
};

```

## Methods

The following table lists the methods in the `SMS_ClientBaselineStatus` class.

| Method | Description |
| --- | --- |
| [GetClientBaselineStatusSummary Method in Class SMS_ClientBaselineStatus](getclientbaselinestatussummary-method-in-class-sms_clientbaselinestatus) | Gets baseline status summary information by BaselineType and CollectionID. |

## Properties

`BaselineType` Data type: `uint32`

Access type: Read-only

Qualifiers: [read]

The client baseline type. Possible values are:

| Value | Client baseline type |
| --- | --- |
| 1 | Production |
| 2 | Staging |

`InstalledClientVersion` Data type: `String`

Access type: Read/Write

Qualifiers: none

Client version that deployed through client deployment.

`LastErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The last error code sent by the client.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Resource ID of the client.

`SMSID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The SMSID of the client.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The status of the client against the client baseline. Possible values are:

| Value | Client status |
| --- | --- |
| 1 | Compliant |
| 2 | InProgress |
| 3 | NotCompliant |
| 4 | CriticalError |

## Remarks

Class qualifiers for this class include:

- Dynamic

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).