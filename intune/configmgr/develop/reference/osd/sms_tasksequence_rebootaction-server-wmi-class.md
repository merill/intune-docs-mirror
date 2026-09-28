---
layout: Conceptual
title: SMS_TaskSequence_RebootAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_rebootaction-server-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn about the simplified syntax, methods, properties, and requirements of the SMS_TaskSequence_RebootAction server class.
locale: en-us
document_id: f14db1d7-9a6a-1ab8-cd02-f916bafffc0b
document_version_independent_id: a075f0dd-6499-08ae-e8ee-5560d6719b77
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_rebootaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_rebootaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_rebootaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6c94b586-d8cf-65a0-643a-7625c892bdd7
---

# SMS_TaskSequence_RebootAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_RebootAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that specifies restart options for the target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_RebootAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Message;
      UInt32 MessageTimeout;
      String Name;
      String SupportedEnvironment;
      String Target;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_RebootAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Message` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-512")]

A user-defined message for display in the reboot dialog box. The message length can be between 0 and 512 characters.

`MessageTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [VariableName("SMSRebootTimeout")]

The number of seconds that a user-defined message is displayed to the user before the computer restarts. Specify 0 seconds (default) to indicate that no reboot message should be displayed.

The task sequence variable that is associated with this property is SMSRebootTimeout. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Target` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, CommandLineArg(1)]

The operating system to use for reboot. Possible values are:

- HD
- WinPE

    `Timeout` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

[CommandLine("smsboot.exe /target:%1"),VariablePrefix("SMSReboot"),

ActionCategory("General,6,1"),ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "RebootComputerControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).