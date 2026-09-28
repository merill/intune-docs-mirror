---
layout: Conceptual
title: SMS_CIDeploymentUnknownStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_cideploymentunknownstatus-server-wmi-class
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
description: Learn how to represent the status of a configuration item deployment for unknown status using SMS_CIDeploymentUnknownStatus class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6a898dc6-e596-aa63-7a96-92726d58fa4d
document_version_independent_id: 36402904-79d9-19ec-a115-66892e936784
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_cideploymentunknownstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_cideploymentunknownstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_cideploymentunknownstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f8d00545-437e-e384-249a-6e795b83468d
---

# SMS_CIDeploymentUnknownStatus Class - Configuration Manager | Microsoft Learn

The `SMS_CIDeploymentUnknownStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the status of a configuration item deployment for unknown status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIDeploymentUnknownStatus : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 Category;
    UInt32 CI_ID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentIntent;
    UInt32 PolicyModelID;
    String SoftwareName;
    DateTime StartTime;
    UInt32 Total;
};
```

## Methods

The `SMS_CIDeploymentUnknownStatus` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`Category` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Status category.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DeploymentIntent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Model ID of the policy.

`SoftwareName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the software.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`Total` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Total number of resources in this state.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).