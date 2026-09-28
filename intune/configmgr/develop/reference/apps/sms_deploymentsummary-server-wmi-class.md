---
layout: Conceptual
title: SMS_DeploymentSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class
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
description: In Configuration Manager, the SMS_DeploymentSummary Windows Management Instrumentation class is an SMS Provider server class that represents an application, SUM or classic program deployment summary.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4ecf07a4-294e-a82e-6412-75135212665b
document_version_independent_id: d1d25be8-a82f-8d34-db89-34a0ca1a254b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 580622d5-53eb-c02f-15e6-8f70deb4a6ca
---

# SMS_DeploymentSummary Class - Configuration Manager | Microsoft Learn

The `SMS_DeploymentSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an application, SUM or classic program deployment summary.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeploymentSummary : SMS_BaseClass
{
    String ApplicationName;
    UInt32 AssignmentID;
    UInt32 CI_ID;
    String CollectionID;
    String CollectionName;
    DateTime CreationTime;
    String DeploymentID;
    UInt32 DeploymentIntent;
    DateTime DeploymentTime;
    SInt32 DesiredConfigType;
    DateTime EnforcementDeadline;
    UInt32 FeatureType;
    String ModelName;
    DateTime ModificationTime;
    SInt32 NumberErrors;
    SInt32 NumberInProgress;
    SInt32 NumberOther;
    SInt32 NumberSuccess;
    SInt32 NumberTargeted;
    SInt32 NumberUnknown;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 PolicyModelID;
    String ProgramName;
    String SecuredObjectId;
    String SoftwareName;
    DateTime SummarizationTime;
    UInt32 SummaryType;
};
```

## Methods

The following table lists the methods in the `SMS_DeploymentSummary` class.

| Method | Description |
| --- | --- |
| [UpdateClassicDeployment Method in Class SMS_DeploymentSummary](updateclassicdeployment-method-in-class-sms_deploymentsummary) | Updates the summarized results for a specific Classic Deployment. |
| [UpdateDeployment Method in Class SMS_DeploymentSummary](updatedeployment-method-in-class-sms_deploymentsummary) | Updates the summarized results for a specific Classic Deployment. |

## Properties

`ApplicationName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the application.

`AssignmentID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifier for the collection where the deployment was deployed.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection to which the deployment was deployed.

`CreationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DeploymentID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique auto-generated key to identify the deployment.

`DeploymentIntent` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DeploymentTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time that the deployment started.

`DesiredConfigType` Data type: `SInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`FeatureType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Feature type. Possible values are:

| Value | Feature type |
| --- | --- |
| 1 | Application |
| 2 | Program |
| 3 | MobileProgram |
| 4 | Script |
| 5 | SoftwareUpdate |
| 6 | Baseline |
| 7 | TaskSequence |
| 8 | ContentDistribution |
| 9 | DistributionPointGroup |
| 10 | DistributionPointHealth |
| 11 | ConfigurationPolicy |
| 28 | AbstractConfigurationItem |

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModificationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time that the deployment was last modified.

`NumberErrors` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients with an error when installing the deployment.

`NumberInProgress` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients with the deployment in progress.

`NumberOther` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients where the requirements are not met for the deployment.

`NumberSuccess` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that successfully installed the deployment.

`NumberTargeted` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients targeted for installation of the deployment.

`NumberUnknown` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients whose compliance state is unknown for the deployment.

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Secured object class ID. Possible values are:

| Value | Secured object class ID |
| --- | --- |
| 200 | SMS\_CIAssignment |
| 201 | SMS\_Advertisement |

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Identifier of the program (for Configuration Manager 2007 deployments).

`PolicyModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy model identifier.

`ProgramName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the program (for Configuration Manager 2007 deployments).

`SecuredObjectId` Data type: `String`

Access type: Read/Write

Qualifiers: none

ID of the secured object.

`SoftwareName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the software.

`SummarizationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Summarization time.

`SummaryType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Summary type.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).