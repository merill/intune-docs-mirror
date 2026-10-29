---
layout: Conceptual
title: SMS_SUMDeploymentAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_sumdeploymentassetdetails-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents per-asset details for SUM deployments in-console monitoring.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 09be9415-c901-b5d4-c99f-4086136344a2
document_version_independent_id: 021e0732-9ee4-722c-1a3e-0f2499c6b1cb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_sumdeploymentassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_sumdeploymentassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_sumdeploymentassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 8f1238f9-d694-f4b3-cc08-767b8f67d17c
---

# SMS_SUMDeploymentAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_SUMDeploymentAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents per-asset details for SUM deployments in-console monitoring.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SUMDeploymentAssetDetails : SMS_BaseClass  
{  
    UInt32 AssignmentID;  
    String AssignmentName;  
    String AssignmentUniqueID;  
    String CollectionID;  
    String CollectionName;  
    String DeviceName;  
    UInt32 IsCompliant;  
    Boolean IsMachineAssignedToUser;  
    Boolean IsMachineChangesPersisted;  
    Boolean IsVM;  
    String LastComplianceMessageDesc;  
    UInt32 LastComplianceMessageID;  
    DateTime LastComplianceMessageTime;  
    UInt32 LastEnforcementErrorCode;  
    UInt32 LastEnforcementErrorID;  
    DateTime LastEnforcementErrorTime;  
    String LastEnforcementMessageDesc;  
    UInt32 LastEnforcementMessageID;  
    DateTime LastEnforcementMessageTime;  
    UInt32 ResourceID;  
    String StatusDescription;  
    UInt32 StatusEnforcementState;  
    UInt32 StatusErrorCode;  
    DateTime StatusTime;  
    UInt32 StatusType;  
    String UserID;  
    String VMHostName;  
};  
```

## Methods

The `SMS_SUMDeploymentAssetDetails` class does not define any methods.

## Properties

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

`DeviceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the device.

`IsCompliant` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the asset is compliant.

`IsMachineAssignedToUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the computer is assigned to a user.

`IsMachineChangesPersisted` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the virtual machine changes are persisted.

`IsVM` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this is a virtual machine.

`LastComplianceMessageDesc` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Last Compliance Message Description.

`LastComplianceMessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Last compliance message ID.

`LastComplianceMessageTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Last compliance message time.

`LastEnforcementErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Last enforcement error code.

`LastEnforcementErrorID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Last enforcement error ID.

`LastEnforcementErrorTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Last enforcement error time.

`LastEnforcementMessageDesc` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Last enforcement message description.

`LastEnforcementMessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Last enforcement message ID.

`LastEnforcementMessageTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Last enforcement message time.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Unique Configuration Manager-supplied ID for the resource.

`StatusDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the status.

`StatusEnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Additional enforcement state for progress and error status (0 for others).

`StatusErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Additional error code for error status (0 for others).

`StatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Status time.

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, not\_null, read]

Status type. Possible values are:

| Value | Status |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 4 | Unknown |
| 5 | Error |

`UserID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Identifier of the user.

`VMHostName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of virtual machine host.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).