---
layout: Conceptual
title: SMS_AzureServicesTask Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_azureservicestask-server-wmi-class
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
description: An SMS Provider server class that represents a Microsoft Azure specific operation that can be performed on the specified Microsoft Azure service. This class can be used to initiate an operation and monitor the results of the operation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6a01acca-0026-bfb7-7fbf-1c5130c085dc
document_version_independent_id: e14df595-18ba-7377-77bc-a5a5aa9e16ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_azureservicestask-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_azureservicestask-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_azureservicestask-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 7871aa9d-f23a-7743-dda6-561666bba794
---

# SMS_AzureServicesTask Class - Configuration Manager | Microsoft Learn

The `SMS_AzureServicesTask` WMI class is an SMS Provider server class in Configuration Manager, that represents a Microsoft Azure specific operation that can be performed on the specified Microsoft Azure service. This can be used to initiate an operation and monitor the results of the operation.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AzureServicesTask : SMS_BaseClass
{
    UInt32 AzureServiceId;
    String SiteCode;
    DateTime TaskCreationTime;
    DateTime TaskEndTime;
    UInt32 TaskID;
    String TaskKeyValue;
    UInt32 TaskStateId;
    UInt32 TaskTypeId;
    UInt32 Type;
};
```

## Methods

The `SMS_AzureServicesTask` class doesn't define any methods.

## Properties

`AzureServiceId` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The service identifier key for the `SMS_AzureService` instance on which the current task will be performed.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Site code of the site that owns the task.

`TaskCreationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time the task was created.

`TaskEndTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time the task ended.

`TaskID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, not\_null]

Identifier of the Microsoft Azure service task.

`TaskKeyValue` Data type: `String`

Access type: Read/Write

Qualifiers: none

Input for the task - if necessary. This value isn't needed for `CreateDeployment`, `UpgradeDeployment`, `DeleteDeployment`, `StopDeployment`, or `StartDeployment` and any value will be ignored.

`TaskStateId` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [values]

Identifier of the current task state. Possible values are:

| Value | Task state |
| --- | --- |
| 1 | Created |
| 2 | In Progress |
| 3 | Completed |
| 4 | Failed |

`TaskTypeId` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, values]

Identifier for type of task. Possible values are:

| Value | Task type |
| --- | --- |
| 1 | CreateDeployment |
| 2 | UpgradeDeployment |
| 3 | DeleteDeployment |
| 4 | StopDeployment |
| 5 | StartDeployment |

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Type of task. Possible values are:

| Value | Task type |
| --- | --- |
| 0 | RunOnce |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).