---
layout: Conceptual
title: SMS_AppDependencyData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_appdependencydata-server-wmi-class
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
description: The `SMS_AppDependencyData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents application deployment dependency data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f7bf5b3d-7b3a-199a-a5a6-9da6fde5aa8b
document_version_independent_id: a47db8e0-bd4e-3dde-cb6f-78af2551fb91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_appdependencydata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_appdependencydata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_appdependencydata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 38bf341c-e717-69b0-63f4-d723e7079c80
---

# SMS_AppDependencyData Class - Configuration Manager | Microsoft Learn

The `SMS_AppDependencyData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents application deployment dependency data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AppDependencyData : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    UInt32 ComplianceState;
    String DependencyGroup;
    String DependentDTName;
    UInt32 DTCI;
    UInt32 DTModelID;
    UInt64 DTResultID;
    UInt32 EnforcementState;
    UInt32 ErrorValue;
    String MachineName;
    String UserName;
};
```

## Methods

The `SMS_AppDependencyData` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class)..

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DependencyGroup` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Name of the Dependency group.

`DependentDTName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Name of the dependent deployment type.

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`EnforcementState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

Enforcement state. Possible values are:

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

`ErrorValue` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Last return value.

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

Name of the computer that created the message.

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).