---
layout: Conceptual
title: SMS_TaskSequence_OSExpressionGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class
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
description: In Configuration Manager, the SMS_TaskSequence_OSExpressionGroup WMI class is an SMS Provider server class that represents an evaluation of a single operating system platform in a task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 27ab5943-b3a7-198f-8c77-a2c93a09df08
document_version_independent_id: 0cedd4b1-15bb-8b90-e73b-7017d0e1f613
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 1d3036bc-8230-e1d6-27cc-c9da4126929f
---

# SMS_TaskSequence_OSExpressionGroup Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_OSExpressionGroup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an evaluation of a single operating system platform in a task sequence. An object of this type is always contained by an [SMS_TaskSequence_OSConditionGroup Server WMI Class](sms_tasksequence_osconditiongroup-server-wmi-class) object.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_OSExpressionGroup : SMS_TaskSequence_ConditionOperator
{
      String Name;
      SMS_TaskSequence_WMIConditionExpression Operands[];
      String OperatorType;
      String PlatformArchKey;
      String PlatformMaxVerKey;
      String PlatformMinVerKey;
      String PlatformTypeKey;
};
```

## Methods

The `SMS_TaskSequence_OSExpressionGroup` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional. The name of an operating system, for example, "Windows XP SP2". The default value is "". See the `DisplayText` property for `SMS_SupportedPlatforms`.

`Operands` Data type: `SMS_TaskSequence_WMIConditionExpression`Array

Access type: Read/Write

Qualifiers: [Not\_NULL]

See [SMS_TaskSequence_ConditionOperator Server WMI Class](sms_tasksequence_conditionoperator-server-wmi-class).

Each element of this property is an [SMS_TaskSequence_WMIConditionExpression Server WMI Class](sms_tasksequence_wmiconditionexpression-server-wmi-class) object that matches the WQL query for the `SMS_SupportedPlatforms` Server WMI Class object indexed by the platform keys. The expressions are typically built from the WQL query stored in the `Condition` property of `SMS_SupportedPlatforms`. There must be at least one [SMS_TaskSequence_WMIConditionExpression Server WMI Class](sms_tasksequence_wmiconditionexpression-server-wmi-class) contained by the [SMS_TaskSequence_OSExpressionGroup Server WMI Class](sms_tasksequence_osexpressiongroup-server-wmi-class).

`OperatorType` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_NULL]

See [SMS_TaskSequence_ConditionOperator Server WMI Class](sms_tasksequence_conditionoperator-server-wmi-class).

The only operator type supported by this class is "and".

`PlatformArchKey` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Platform key that maps to the `OSPlatform` property for `SMS_SupportedPlatforms` objects. For more information, see the Remarks section later in this topic.

`PlatformMaxVerKey` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Platform key that maps to the `OSMaxVersion` property for `SMS_SupportedPlatforms` objects. For more information, see the Remarks section later in this topic.

`PlatformMinVerKey` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Platform key that maps to the `OSMinVersion` property for SMS\_SupportedPlatforms objects. For more information, see the Remarks section later in this topic.

`PlatformTypeKey` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Platform key that maps to the `OSName` property for `SMS_SupportedPlatforms` objects. For more information, see the Remarks section later in this topic.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

The platform strings specified by `PlatformArchKey`, `PlatformMaxVerKey`, `PlatformMinVerKey`, and `PlatformTypeKey` are used to index the corresponding `SMS_SupportedPlatforms` object instance for the expression.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).