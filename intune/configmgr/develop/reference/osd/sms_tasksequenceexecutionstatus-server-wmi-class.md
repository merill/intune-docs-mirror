---
layout: Conceptual
title: SMS_TaskSequenceExecutionStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequenceexecutionstatus-server-wmi-class
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
description: In Configuration Manager, The SMS_TaskSequenceExecutionStatus WMI class is an SMS Provider server class that represents the status of an execution of a task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 249a8063-512a-1427-deb8-92be72a76f8f
document_version_independent_id: 8f8bebf3-4abc-7832-e05a-836ad5b3c41b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequenceexecutionstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequenceexecutionstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequenceexecutionstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 07e691d5-0b03-8e95-1180-4bd2a2cc76dd
---

# SMS_TaskSequenceExecutionStatus Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequenceExecutionStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the status of an execution of a task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceExecutionStatus : SMS_BaseClass
{
    String ActionName;
    String ActionOutput;
    String AdvertisementID;
    DateTime ExecutionTime;
    UInt32 ExitCode;
    String GroupName;
    UInt32 LastStatusMsgID;
    String LastStatusMsgName;
    String PackageID;
    UInt32 ResourceID;
    UInt32 Step;
};
```

## Methods

The `SMS_TaskSequenceExecutionStatus` class does not define any methods.

## Properties

`ActionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the action in the task sequence that was executed.

`ActionOutput` Data type: `String`

Access type: Read/Write

Qualifiers: none

Console output of the task sequence step that was executed.

`AdvertisementID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Deployment identifier of the task sequence.

`ExecutionTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [key]

Run time of the task sequence.

`ExitCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Exit code of the task sequence step that was executed.

`GroupName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Group name in the task sequence that was executed.

`LastStatusMsgID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier for this execution status.

`LastStatusMsgName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name for this execution status.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Task sequence package identifier.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Client computer identifier.

`Step` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Step number in the task sequence that was executed.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).