---
layout: Conceptual
title: SMS_AppDeploymentRequirementsNotMetAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentrequirementsnotmetassetdetails-server-wmi-class
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
description: Learn how to use the SMS_AppDeploymentRequirementsNotMetAssetDetails class to represent asset-level details of application deployments where requirements are not met.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0e2fa076-5f2b-0bca-a1e5-fa74d1486e00
document_version_independent_id: 046134ef-a65d-8b0a-21e6-c4ff5d86ad55
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_appdeploymentrequirementsnotmetassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_appdeploymentrequirementsnotmetassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_appdeploymentrequirementsnotmetassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7348a6be-ed34-3b17-9ef3-644512ff906f
---

# SMS_AppDeploymentRequirementsNotMetAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_AppDeploymentRequirementsNotMetAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents asset-level details of application deployments where requirements are not met.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDeploymentRequirementsNotMetAssetDetails : SMS_BaseClass
{
    UInt32 AppCI;
    String AppName;
    UInt32 AppStatusType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String CollectionName;
    String CurrentReqValue;
    UInt32 DeploymentIntent;
    UInt32 DTCI;
    UInt32 DTModelID;
    String DTName;
    UInt32 DTPresent;
    UInt64 DTResultID;
    UInt32 EnforcementState;
    UInt32 ExtendedInfoDescriptionID;
    UInt32 ExtendedInfoID;
    Boolean IsMachineAssignedToUser;
    Boolean IsMachineChangesPersisted;
    Boolean IsVM;
    UInt32 MachineID;
    String MachineName;
    String MachineOS;
    UInt32 PolicyModelID;
    String RequirementName;
    UInt32 RequirementType;
    UInt32 Revision;
    UInt32 RuleID;
    DateTime StartTime;
    UInt32 StatusType;
    String Technology;
    String UniqueRequirementName;
    UInt32 UpdateState;
    String UserName;
    String VMHostName;
};
```

## Methods

The `SMS_AppDeploymentRequirementsNotMetAssetDetails` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AppName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AppStatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`CurrentReqValue` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Current requirement value.

`DeploymentIntent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTPresent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Deployment type present.

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [not\_null, read]

Deployment type result identifier.

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

Enforcement state. Possible values are:

| Value | Enforcement state |
| --- | --- |
| 0 | Enforcement state unknown |
| 1 | Enforcement started |
| 2 | Enforcement waiting for content |
| 3 | Waiting for another installation to complete |
| 4 | Waiting for maintenance window before installing |
| 5 | Restart required before installing |
| 6 | General failure |
| 7 | Pending installation |
| 8 | Installing update |
| 9 | Pending system restart |
| 10 | Successfully installed update |
| 11 | Failed to install update |
| 12 | Downloading update |
| 13 | Downloaded update |
| 14 | Failed to download update |

`ExtendedInfoDescriptionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`ExtendedInfoID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`IsMachineAssignedToUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`IsMachineChangesPersisted` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`IsVM` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`MachineID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`MachineOS` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Computer operating system.

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`RequirementName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of requirement.

`RequirementType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Type of requirement that has not been met. Possible values are:

| Value | Type of requirement violation |
| --- | --- |
| 0 | Constraint violation |
| 1 | Conflict violation |
| 2 | Enforcement violation |
| 3 | Requirement violation |
| 4 | Dependency violation |

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`RuleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Rule ID of the requirement that has not been met.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`Technology` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`UniqueRequirementName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of unique requirement.

`UpdateState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`VMHostName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).