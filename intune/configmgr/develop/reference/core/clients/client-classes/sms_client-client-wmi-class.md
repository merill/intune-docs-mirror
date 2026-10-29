---
layout: Conceptual
title: SMS_Client Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class
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
description: Article describing the use of SMS_CLient class in Configuration Manager to represent the client and facilitate manipulation and retrieval of client information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a568e8f9-269f-0380-c7a6-a8708e48c3b0
document_version_independent_id: 855377fe-fdae-df0f-1b7e-b35af17891fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: fe271bd5-73ee-7b16-bedb-a7f7eb07b04d
---

# SMS_Client Class - Configuration Manager | Microsoft Learn

The `SMS_Client` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents the client and facilitates manipulation and retrieval of client information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```syntax
Class SMS_Client
{
      Boolean AllowLocalAdminOverride;
      UInt32 ClientType;
      String ClientVersion;
      Boolean EnableAutoAssignment;
};
```

## Methods

The following table shows the methods in `SMS_Client`.

| Method | Description |
| --- | --- |
| [EvaluateMachinePolicy Method in Class SMS_Client](evaluatemachinepolicy-method-in-class-sms_client) | Initiates the evaluation of the policy assigned to a specified computer or device. |
| [GetAssignedSite Method in Class SMS_Client](getassignedsite-method-in-class-sms_client) | Gets the current assigned site of the client. |
| [RequestMachinePolicy Method in Class SMS_Client](requestmachinepolicy-method-in-class-sms_client) | Initiates a request for machine policy. |
| [ResetPolicy Method in Class SMS_Client](resetpolicy-method-in-class-sms_client) | Resets the policy on a client. |
| [SetAssignedSite Method in Class SMS_Client](setassignedsite-method-in-class-sms_client) | Sets the client's assigned site. |
| **SetClientProvisioningMode** | Reserved. |
| [SetGlobalLoggingConfiguration Method in Class SMS_Client](setgloballoggingconfiguration-method-in-class-sms_client) | Defines the default logging configuration. |
| [TriggerSchedule Method in Class SMS_Client](triggerschedule-method-in-class-sms_client) | Triggers the client to execute the specified schedule. |

## Properties

### `AllowLocalAdminOverride`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Reserved.

### `ClientType`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Reserved. Always 1.

### `ClientVersion`

Data type: `String`

Access type: Read/Write

Qualifiers: None

Version number of the client.

### `EnableAutoAssignment`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if automatic assignment is enabled.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).