---
layout: Conceptual
title: SMS_TaskSequence_SetVariableAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class
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
description: An SMS Provider server class that represents a task sequence action. It sets the value of a task sequence environment variable.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 611260d5-c85f-329b-e6c8-a5f3a89f855a
document_version_independent_id: 8e4ef110-6187-8ff8-6615-c4617853eff0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class.md
cmProducts: []
platformId: 8d7179ed-c416-d49c-bd59-4071fe406b87
---

# SMS_TaskSequence_SetVariableAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_SetVariableAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that sets the value of a task sequence environment variable.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_SetVariableAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean DoNotShowVariableValue;
      Boolean Enabled;
      string HiddenVariableValue;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      String VariableName;
      String VariableValue;
};
```

## Methods

The `SMS_TaskSequence_SetVariableAction` class doesn't define any methods.

## Properties

### `Condition`

Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `ContinueOnError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Description`

Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `DoNotShowVariableValue`

Data type: `Boolean`

Access type: Read/write

Default value `false`. This property corresponds to the setting in the task sequence editor, **Do not display this value**.

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `HiddenVariableValue`

Data type: `String`

Access type: Read/write

Hidden value of the task sequence environment variable. The value length must be between 0 and 4,001 characters.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `VariableName`

Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(1), Not\_Null, AllowedLen("1-256")]

Name of the task sequence environment variable to set. The name length must be between 1 and 256 characters.

### `VariableValue`

Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(2), Not\_Null, AllowedLen("0-4001")]

Value of the task sequence environment variable. The value length must be between 0 and 4,001 characters.

## Remarks

Class qualifiers for this class include:

```
[CommandLine("tsenv.exe \\"%1=%2\\""),

ActionCategory{"General,7,1"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "SetSequenceVariableControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).