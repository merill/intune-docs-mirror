---
layout: Conceptual
title: SMS_CIDeploymentUnknownAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_cideploymentunknownassetdetails-server-wmi-class
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
description: The SMS_CIDeploymentUnknownAssetDetails WMI class represents the asset-level status of a configuration item deployment for unknown status.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 68b8c43a-550b-a5b6-f8f9-8d477222c32c
document_version_independent_id: 1d5ec63e-2710-8224-602e-ff423c9efeaf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_cideploymentunknownassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_cideploymentunknownassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_cideploymentunknownassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 50063639-d654-f1e1-44ee-dbfec470fd58
---

# SMS_CIDeploymentUnknownAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_CIDeploymentUnknownAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the asset-level status of a configuration item deployment for unknown status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIDeploymentUnknownAssetDetails : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 Category;
    UInt32 CI_ID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentIntent;
    Boolean IsMachineAssignedToUser;
    Boolean IsMachineChangesPersisted;
    Boolean IsVM;
    UInt32 MachineID;
    String MachineName;
    String MachineOS;
    UInt32 PolicyModelID;
    String SoftwareName;
    DateTime StartTime;
    String UserName;
    String VMHostName;
};
```

## Methods

The `SMS_CIDeploymentUnknownAssetDetails` class does not define any methods.

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

Qualifiers: [read]

Category description.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Unique ID of the configuration item. This ID is unique only for the site.

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

Qualifiers: [read]

Computer operating system.

`PolicyModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`SoftwareName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the software.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

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