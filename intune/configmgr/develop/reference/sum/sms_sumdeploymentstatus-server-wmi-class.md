---
layout: Conceptual
title: SMS_SUMDeploymentStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_sumdeploymentstatus-server-wmi-class
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
description: The SMS_SUMDeploymentStatus WMI class represents per-deployment-state summary for SUM deployments in-console monitoring.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 939c8d0e-15ab-27d9-d73b-1181437371dc
document_version_independent_id: dbedcdad-f587-b1e3-59b8-6faef8e9100f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_sumdeploymentstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_sumdeploymentstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_sumdeploymentstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d5f79099-7e4f-f8ca-798b-657d25d4e0f9
---

# SMS_SUMDeploymentStatus Class - Configuration Manager | Microsoft Learn

The `SMS_SUMDeploymentStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents per-deployment-state summary for SUM deployments in-console monitoring.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SUMDeploymentStatus : SMS_BaseClass  
{  
    UInt32 Assets;  
    UInt32 AssignmentID;  
    String AssignmentName;  
    String AssignmentUniqueID;  
    String CollectionID;  
    String CollectionName;  
    DateTime LastStatusTime;  
    String StatusDescription;  
    UInt32 StatusEnforcementState;  
    UInt32 StatusErrorCode;  
    UInt32 StatusType;  
    DateTime SummarizationTime;  
};  
```

## Methods

The `SMS_SUMDeploymentStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Number of assets related to the status.

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

The ID of the configuration item assignment. This ID is unique only for the site.

`AssignmentName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The local assignment name.

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The unique ID of the configuration item assignment. This ID is unique across sites.

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Existing collection to which the deployment is being targeted.

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the collection to which the deployment is being targeted.

`LastStatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Last status time.

`StatusDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the status.

`StatusEnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Additional enforcement state for progress and error status (0 for others).

`StatusErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Additional error code for error status (0 for others).

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, key, read]

Status type. Possible values are:

| Value | Status |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 4 | Unknown |
| 5 | Error |

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The last time the summarization task was run for this application.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).