---
layout: Conceptual
title: SMS_TaskSequence_OSConditionGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class
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
description: Learn how to use Configuration Manager SMS_TaskSequence_OSConditionGroup Windows Management Instrumentation (WMI) class  to represent an evaluation of a group of operating system platforms.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fe6da475-d584-e2a4-ee3b-fe57a68b3f00
document_version_independent_id: e33ff3f4-bc52-9ec5-26b2-ad86036de7e2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 79db5cd6-4f59-f0d2-8a14-8cc83a9ef749
---

# SMS_TaskSequence_OSConditionGroup Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_OSConditionGroup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an evaluation of a group of operating system platforms, for example, Windows Vista, in a task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_OSConditionGroup : SMS_TaskSequence_ConditionOperator
{
      SMS_TaskSequence_OSExpressionGroup Operands[];
      String OperatorType;
};
```

## Methods

The `SMS_TaskSequence_OSConditionGroup` class does not define any methods.

## Properties

`Operands` Data type: `SMS_TaskSequence_OSExpressionGroup`Array

Access type: Read/Write

Qualifiers: [Not\_NULL]

An array of supported operating system platforms to evaluate. Stored in a

[SMS_TaskSequence_OSExpressionGroup Server WMI Class](sms_tasksequence_osexpressiongroup-server-wmi-class) array. There must be at least one array member.

`OperatorType` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_NULL]

See [SMS_TaskSequence_ConditionOperator Server WMI Class](sms_tasksequence_conditionoperator-server-wmi-class).

Only the operator "or" is supported.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).