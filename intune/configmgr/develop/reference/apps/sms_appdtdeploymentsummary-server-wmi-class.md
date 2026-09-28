---
layout: Conceptual
title: SMS_AppDTDeploymentSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdtdeploymentsummary-server-wmi-class
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
description: Learn how to use the SMS_AppDTDeploymentSummary class to represent the deployment type-level summary of application deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7c9debc6-f79e-ae93-1159-f598a47fc5ca
document_version_independent_id: ce29eb51-8c75-164b-1afe-20fee775c74b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_appdtdeploymentsummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_appdtdeploymentsummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_appdtdeploymentsummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 47fbaa25-301d-7696-4180-e5b7a804c746
---

# SMS_AppDTDeploymentSummary Class - Configuration Manager | Microsoft Learn

The `SMS_AppDTDeploymentSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the deployment type-level summary of application deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDTDeploymentSummary : SMS_BaseClass
{
    UInt32 AppCI;
    String AppModelName;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentIntent;
    DateTime DeploymentTime;
    String Description;
    UInt32 DTCI;
    String DTModelName;
    DateTime ModificationTime;
    SInt32 NumberAlreadyPresent;
    SInt32 NumberErrors;
    SInt32 NumberInProgress;
    SInt32 NumberInstalled;
    SInt32 NumberReqsNotMet;
    DateTime SummarizationTime;
    String Technology;
};
```

## Methods

The `SMS_AppDTDeploymentSummary` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AppModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model Name of the application.

`AssignmentID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).The ID of the collection to which the deployment was deployed.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DeploymentIntent` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DeploymentTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time the deployment was created.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the deployment type.

`DTCI` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model name of the deployment type.

`ModificationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time that the deployment type was last modified.

`NumberAlreadyPresent` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that have this deployment type installed.

`NumberErrors` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that return an error during an installation.

`NumberInProgress` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that have this deployment type installation in progress.

`NumberInstalled` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that have this deployment type installed.

`NumberReqsNotMet` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that do not meet the requirements of this deployment type.

`SummarizationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time when summarization occurs.

`Technology` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).