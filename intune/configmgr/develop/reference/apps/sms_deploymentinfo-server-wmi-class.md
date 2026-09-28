---
layout: Conceptual
title: SMS_DeploymentInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymentinfo-server-wmi-class
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
description: The SMS_DeploymentInfo Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents information for all types of deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ef72d080-59b8-fbc2-1e61-30a8d2b3551e
document_version_independent_id: 989dbf20-4208-f6f4-e44d-199afdc60eb6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_deploymentinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_deploymentinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_deploymentinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e805614-09e6-2814-9f3e-d2421f5d534e
---

# SMS_DeploymentInfo Class - Configuration Manager | Microsoft Learn

The `SMS_DeploymentInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents information for all types of deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeploymentInfo : SMS_BaseClass
{
    String CollectionID;
    String CollectionName;
    String DeploymentID;
    UInt32 DeploymentIntent;
    String DeploymentName;
    UInt32 DeploymentType;
    UInt32 DeploymentTypeID;
    String TargetID;
    String TargetName;
    UInt32 TargetSecurityTypeID;
    String TargetSubName;
};
```

## Methods

The following table lists the methods in the `SMS_DeploymentInfo` class.

| Method | Description |
| --- | --- |
| [GetDeployments Method in Class SMS_Deployment_Info](getdeployments-method-in-class-sms_deployment_info) | Gets advertisement identifier or Assignment identifier and related type for a deployment that is deployed to the specified resource. |

## Properties

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Existing collection to which the advertisement is targeted.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection to which the advertisement is advertising.

`DeploymentID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique auto-generated key.

`DeploymentIntent` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Purpose of the deployment.

`DeploymentName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Plain-text name of the deployment (advertisement/assignment).

`DeploymentType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Deployment type.

`DeploymentTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration, key]

Type identifier of the deployment.

`TargetID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier of the target. For package, it's package ID, for a configuration item, it's the Unique\_ID.

`TargetName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Package name, if the target is a package. Application name, if it's an application. Update name, if it's an update.

`TargetSecurityTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Security type identifier of the deployment. For example, if it's a package, this value is 2.

`TargetSubName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Program name if it's a package, otherwise leave this value is empty.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).