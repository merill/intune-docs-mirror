---
layout: Conceptual
title: SMS_TaskSequence_Condition Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class
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
description: In Configuration Manager, the SMS_TaskSequence_Condition Server WMI Class WMI class is an SMS Provider server class that defines a condition for an operating system deployment step.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d1cf1603-6085-9359-c3b4-fe1f8fa7deb4
document_version_independent_id: 35d12b6c-2889-3d9d-fd90-420e2040c660
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_condition-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e93f3d5f-c77d-4365-a7fb-c9f2234416c7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/62e8d07a-cc62-4934-b30b-e168a571e51d
platformId: c47b75a2-229f-2b2d-8b3c-5b1d902285dc
---

# SMS_TaskSequence_Condition Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_Condition Server WMI Class` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that defines a condition for an operating system deployment step. This class is the base class for all conditions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_Condition
{
      SMS_TaskSequence_ConditionOperand Operands[];
};
```

## Methods

The `SMS_TaskSequence_Condition` class does not define any methods.

## Properties

`Operands` Data type: `SMS_TaskSequence_ConditionOperand` Array

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

[SMS_TaskSequence_ConditionOperand Server WMI Class](sms_tasksequence_conditionoperand-server-wmi-class) objects indicating condition operands. For example, the array can contain a single expression, such as an [SMS_TaskSequence_WMIConditionExpression Server WMI Class](sms_tasksequence_wmiconditionexpression-server-wmi-class) object. A more complicated condition array can contain a combination of expressions, operators, and operating system condition groups.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class is the root for a hierarchy of operator and expression objects that represent the condition that determines whether a step or group or action should be executed. This class implies an AND operator. Therefore, all child operands in the array must be `true` for the overall condition to be `true`.

For example, you might want to process a step on a computer that must have Microsoft Office 2007 and Windows Vista installed. In this case, you add to the `Operands` property array, a [SMS_TaskSequence_SoftwareConditionExpression Server WMI Class](sms_tasksequence_softwareconditionexpression-server-wmi-class) that defines Microsoft Office 2007 and a [SMS_TaskSequence_OSConditionGroup Server WMI Class](sms_tasksequence_osconditiongroup-server-wmi-class) that defines Windows Vista. The overall condition evaluates to `true` only when the two operands are `true`. That is, when Microsoft Office 2007 is installed on a computer with Windows Vista installed.

For more information about conditions, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).