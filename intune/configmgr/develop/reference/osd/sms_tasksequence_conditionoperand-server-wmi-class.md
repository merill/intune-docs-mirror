---
layout: Conceptual
title: SMS_TaskSequence_ConditionOperand Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class
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
description: An SMS Provider server class that's the abstract base class for operators and expressions used by task sequence steps.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5b9abc2a-eab7-653f-80dd-6856f7b4f58d
document_version_independent_id: 76580c14-798a-d880-716d-f28b99f37983
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperand-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: facb55c1-27cf-cc78-54d6-8f6f523a945c
---

# SMS_TaskSequence_ConditionOperand Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ConditionOperand` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager. This class is the abstract base class for operators and expressions that are used by task sequence steps.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ConditionOperand
{
};
```

## Methods

The `SMS_TaskSequence_ConditionOperand` class does not define any methods.

## Properties

The `SMS_TaskSequence_ConditionOperand` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    `SMS_TaskSequence_ConditionOperand` derived classes are used to define condition expressions and operators that determine whether a task sequence step should be run. There are two derived classes.

## SMS\_TaskSequence\_ConditionExpression

[SMS_TaskSequence_ConditionExpression Server WMI Class](sms_tasksequence_conditionexpression-server-wmi-class) is the base class for an expression that must evaluate to `true` before the step can be processed. For example, the derived class [SMS_TaskSequence_RegistryConditionExpression Server WMI Class](sms_tasksequence_registryconditionexpression-server-wmi-class) defines an expression for the existence of a registry key.

## SMS\_TaskSequence\_ConditionOperator

[SMS_TaskSequence_ConditionOperator Server WMI Class](sms_tasksequence_conditionoperator-server-wmi-class) defines a Boolean operator and the expressions that are used to evaluate nested expressions.

These classes can be used to define complex conditions such as `Expression1 and (Expression2 or Expression3)`. For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).