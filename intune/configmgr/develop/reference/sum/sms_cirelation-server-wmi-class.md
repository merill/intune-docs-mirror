---
layout: Conceptual
title: SMS_CIRelation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class
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
description: Learn about the SMS_CIRelation Server Windows Management Instrumentation (WMI) Class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 11a14860-d0e9-e9cc-c800-acc03bbb423e
document_version_independent_id: 0466c567-f89b-828e-907f-9172189d9d7f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cirelation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bf5c96d5-cad3-50ce-3465-ddfd6fc15e17
---

# SMS_CIRelation Class - Configuration Manager | Microsoft Learn

The `SMS_CIRelation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that defines the relationship between two configuration items, for example, the superseding of one item by another.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIRelation : SMS_BaseClass
{
    UInt32 FromCIID;
    Boolean IsBroken;
    Boolean IsVersionSpecific;
    UInt32 Priority;
    UInt32 RelationType;
    UInt32 ToCIID;
};
```

## Methods

The `SMS_CIRelation` class does not define any methods.

## Properties

`FromCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The ID of one of the configuration items. The value of this property usually depends on the value of `ToCIID` in the context specified by `RelationType`. For example, this property can represent a child configuration item ID (FROMCIID) that is derived from a parent configuration item ID (TOCIID).

The ID of a configuration item is represented by the `CI_ID` property of [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, key]

`true` if the relation is broken, otherwise the value will be false.

`IsVersionSpecific` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None.

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None.

One App to deployment type relation (9) has priority.

`RelationType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Type of relationship between configuration items. Possible values are:

| Value | Relationship type |
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

`ToCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The ID for the second configuration item that is related to the first item. The value of this property usually depends on the value of `FromCIID` in the context specified by `RelationType`. For example, this property can represent a parent configuration item ID (TOCIID) from which a child configuration item ID (FROMCIID) is derived.

The ID of a configuration item is represented by the `CI_ID` property of [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is applicable to all types of configuration items, not just software updates. For a discussion of configuration item types, see the `CIType_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).