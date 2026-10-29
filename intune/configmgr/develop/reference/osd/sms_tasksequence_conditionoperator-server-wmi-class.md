---
layout: Conceptual
title: SMS_TaskSequence_ConditionOperator Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class
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
description: An SMS Provider server class that represents an operator to use when evaluating task sequence condition operands.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bf27d9b2-4d00-d281-2cca-2b000ce9d302
document_version_independent_id: dd57c82f-e77a-9d5d-e124-b8bfc0e7568a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 48418536-8341-93f2-fa8c-308500be5ed7
---

# SMS_TaskSequence_ConditionOperator Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ConditionOperator` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an operator to use when evaluating task sequence condition operands.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConditionOperator : SMS_TaskSequence_ConditionOperand
{
      SMS_TaskSequence_ConditionOperand Operands[];
      String OperatorType;
};
```

## Methods

The `SMS_TaskSequence_ConditionOperator` class does not define any methods.

## Properties

`Operands` Data type: `SMS_TaskSequence_ConditionOperand` Array

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

[SMS_TaskSequence_ConditionOperand Server WMI Class](sms_tasksequence_conditionoperand-server-wmi-class) objects to test.

`OperatorType` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Type of operator to use in testing the conditions. Possible values are:

- and
- or
- not

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Note

Task sequence step conditions are defined in [SMS_TaskSequence_Condition Server WMI Class](sms_tasksequence_condition-server-wmi-class).

`SMS_TaskSequence_ConditionOperator` is used to create complete complex conditions that determine if a task sequence step should be processed. The `Operands` array property holds one or more expression ([SMS_TaskSequence_ConditionExpression Server WMI Class](sms_tasksequence_conditionexpression-server-wmi-class)) or operator (`SMS_TaskSequence_ConditionOperator`) operands to evaluate.

Note

Both of these classes derive from SMS[SMS_TaskSequence_ConditionOperand Server WMI Class](sms_tasksequence_conditionoperand-server-wmi-class), the type for the `Operands` property.

The operator used to evaluate the operands is defined by the `OperatorType` property.

For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).