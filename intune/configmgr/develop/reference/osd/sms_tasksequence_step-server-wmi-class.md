---
layout: Conceptual
title: SMS_TaskSequence_Step Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class
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
description: In Configuration Manager, the SMS_TaskSequence_Step WMI class is an SMS Provider server class. This class serves as an abstract base class that represents a single step in a task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: abfe9bce-beae-d21d-e809-bed47d8ec737
document_version_independent_id: a3a0686e-e921-52a3-c03e-d19e2218aed6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3d6aa7c5-7989-d745-4db6-6c2c42be2b07
---

# SMS_TaskSequence_Step Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_Step` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager. This class serves as an abstract base class that represents a single step in a task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_Step
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Name;
};
```

## Methods

The `SMS_TaskSequence_Step` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

Optional. An [SMS_TaskSequence_Condition Server WMI Class](sms_tasksequence_condition-server-wmi-class) object representing a condition that can be used to determine if the step should be processed.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` to continue the task sequence even if the step fails.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

Optional. The description of the step. The description length can be between 0 and 255 characters.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the step should be run. Set this property to `false` to ignore the step completely.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

The name of the step. The name length can be between 1 and 100 characters.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Each step in the task sequence is one of the following:
- An individual action that is run on a computer, represented by a [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class) or derived class. For example, the [SMS_TaskSequence_InstallSoftwareAction Server WMI Class](sms_tasksequence_installsoftwareaction-server-wmi-class) class represents an action that specifies a package and a program to install as part of a task sequence.
- A set of actions in a group, represented by [SMS_TaskSequence_Group Server WMI Class](sms_tasksequence_group-server-wmi-class). Groups are useful ways to organize actions. For example, to conditionally process a set of actions, you could organize the actions into a group and add a condition to the group.

    Each step can be associated with a condition, represented by [SMS_TaskSequence_Condition Server WMI Class](sms_tasksequence_condition-server-wmi-class) that determines whether the step is processed.

    For more information, see Operating System Deployment Task Sequence Object Model.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).