---
layout: Conceptual
title: SMS_AppDeploymentAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class
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
description: The SMS_AppDeploymentAssetDetails WMI class is an SMS Provider server class that represents asset-level details about the deployment.
ms.date: 2020-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 93173219-d3a7-a318-6033-71fca60fe734
document_version_independent_id: b3a5e2f1-3266-cbb3-79f0-05a0e862a7b0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_appdeploymentassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: ebafe70d-111c-5bbd-0bb6-330973b41994
---

# SMS_AppDeploymentAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_AppDeploymentAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents asset-level details about the deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDeploymentAssetDetails : SMS_BaseClass
{
    UInt32 AppCI;
    String AppName;
    UInt32 AppStatusType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String CollectionName;
    UInt32 ComplianceState;
    UInt32 DeploymentIntent;
    UInt32 DTCI;
    UInt32 DTModelID;
    String DTName;
    UInt64 DTResultID;
    UInt32 EnforcementState;
    UInt32 ExtendedInfoDescriptionID;
    UInt32 ExtendedInfoID;
    UInt32 InstalledState;
    Boolean IsMachineAssignedToUser;
    Boolean IsMachineChangesPersisted;
    Boolean IsVM;
    UInt32 MachineID;
    String MachineName;
    UInt32 PolicyModelID;
    UInt32 Revision;
    DateTime StartTime;
    UInt32 StatusType;
    String Technology;
    UInt32 UpdateState;
    String UserName;
    String VMHostName;
};
```

## Methods

The `SMS_AppDeploymentAssetDetails` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Application configuration item.

`AppName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Application description.

`AppStatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Application status type. Possible values are:

| Value | Application status |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | RequirementsNotMet |
| 4 | Unknown |
| 5 | Error |

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

ID of the collection to which the deployment was deployed.

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Collection name.

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Compliance state for the configuration item.

`DeploymentIntent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Intended purpose of the deployment, regardless of the Action (Install or Uninstall) specified. Possible values are:

| Value | Intended purpose |
| --- | --- |
| 1 | Required |
| 2 | Available |
| 3 | Simulate |

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Deployment type configuration item.

`DTModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Deployment Type Model ID.

`DTName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the deployment type.

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [not\_null, read]

Deployment Type Result ID.

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

The enforcement state. Possible values are:

| Value | Enforcement state |
| --- | --- |
| 0 | Enforcement State Unknown |
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

Extended information description ID.

`ExtendedInfoID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Extended information ID.

`InstalledState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Installed state. Possible values are:

| Value | Installed state |
| --- | --- |
| 1 | Uninstall |
| 2 | Install |
| 3 | Unknown |

`IsMachineAssignedToUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the computer is assigned to a user.

`IsMachineChangesPersisted` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if changes made to virtual machine are persisted.

`IsVM` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the computer is a virtual machine.

`MachineID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

ID of the virtual machine.

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Virtual machine name.

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Policy Model ID.

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Revision.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Deployment time.

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Status type.

| Value | Status type |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | RequirementsNotMet |
| 4 | Unknown |
| 5 | Error |

`Technology` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Technology.

`UpdateState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Update state.

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

User name.

`VMHostName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Virtual machine host name.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).