---
layout: Conceptual
title: SMS_TaskSequence_ConditionExpression Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class
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
description: The SMS_TaskSequence_ConditionExpression WMI class is an SMS Provider server class that is the abstract base class for all condition expressions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 69c133a0-19fa-e035-b853-fa7e38a03ade
document_version_independent_id: aa273576-116f-529e-e361-b4d86caa5407
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d1ea00fe-816f-4b7b-b69d-04a16eb65f01
---

# SMS_TaskSequence_ConditionExpression Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ConditionExpression` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is the abstract base class for all condition expressions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConditionExpression : SMS_TaskSequence_ConditionOperand
{
};
```

## Methods

The `SMS_TaskSequence_ConditionExpression` class does not define any methods.

## Properties

The `SMS_TaskSequence_ConditionExpression` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    `SMS_TaskSequence_ConditionExpression` is the abstract base class for an expression that must evaluate to `true`, for the task sequence step to be processed. For example, the derived class [SMS_TaskSequence_RegistryConditionExpression Server WMI Class](sms_tasksequence_registryconditionexpression-server-wmi-class) defines an expression for the existence of a registry key.

    An `SMS_TaskSequence_ConditionExpression` is stored in a condition's ([SMS_TaskSequence_Condition Server WMI Class](sms_tasksequence_condition-server-wmi-class)) `Operands` array property, which defines the list of condition operands.

Note

In a task sequence step ([SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class)), the condition is defined in the `Condition` property.

Alternatively, more complex conditions are created by adding a [SMS_TaskSequence_ConditionOperator Server WMI Class](sms_tasksequence_conditionoperator-server-wmi-class) object to the condition's `Operands` array property, and by adding expressions and operators to the added [SMS_TaskSequence_ConditionOperator Server WMI Class](sms_tasksequence_conditionoperator-server-wmi-class)`Operands` array.

For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).