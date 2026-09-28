---
layout: Conceptual
title: SMS_AppRelation_Flat Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_apprelation_flat-server-wmi-class
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
description: Details of the SMS_AppRelation_Flat WMI class
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3da2414c-01d1-3679-6b10-66b6f4fc796e
document_version_independent_id: e81ea471-73ee-5567-66fa-35e7d315cc71
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_apprelation_flat-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_apprelation_flat-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_apprelation_flat-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 73829f9b-7590-fa33-6633-dd59c0a8bf61
---

# SMS_AppRelation_Flat Class - Configuration Manager | Microsoft Learn

The `SMS_AppRelation_Flat` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the flattened application relation. This includes direct and indirect relations.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AppRelation_Flat : SMS_BaseClass
{
    UInt32 FromApplicationCIID;
    UInt32 FromDeploymentTypeCIID;
    UInt32 Level;
    UInt32 RelationType;
    UInt32 ToApplicationCIID;
    UInt32 ToDeploymentTypeCIID;
};
```

## Methods

The `SMS_AppRelation_Flat` class does not define any methods.

## Properties

`FromApplicationCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

From-application configuration item identifier.

`FromDeploymentTypeCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

From-deployment type identifier.

`Level` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Level between the from-deployment type and the to-deployment type.

`RelationType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Type of relationship between configuration items. Possible values are:

| Value | Relationship |
| --- | --- |
| 1 | Bundled |
| 2 | Required |
| 3 | Prohibited |
| 4 | Optional |
| 5 | Derived |
| 6 | Superseded |
| 7 | Self |
| 8 | Reference |
| 9 | AppToDTReference |
| 10 | AppDependence |
| 11 | Intention |
| 12 | Platform |
| 13 | GlobalConditionReference |
| 15 | ApplicationSuperSeded |
| 16 | ApplicationType |
| 17 | ApplicationHost |
| 18 | ApplicationInstaller |
| 19 | SupersedOrDependent |
| 20 | VirtualEnvironmentReference |
| 21 | AppDCMReference |
| 22 | DeploymentTypeToPolicyTemplateReference |
| 23 | CIInheritanceRelation |
| 24 | AppConfigTemplateReference |
| 25 | AppGroupItemReference |

`ToApplicationCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

To-application configuration item identifier.

`ToDeploymentTypeCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

To-deployment type configuration item identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).