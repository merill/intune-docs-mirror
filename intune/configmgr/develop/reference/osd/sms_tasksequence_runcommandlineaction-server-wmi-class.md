---
layout: Conceptual
title: SMS_TaskSequence_RunCommandLineAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class
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
description: an SMS Provider server class in Configuration Manager. It represents a task sequence action that runs a user-specified command line.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 50a63791-6f1d-4984-a2a2-8c859e236662
document_version_independent_id: f8f64598-39ef-7107-f199-c62b332dbd61
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class.md
cmProducts: []
platformId: ff907a6e-ebd0-dc99-e58f-7ed36a1f7094
---

# SMS_TaskSequence_RunCommandLineAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_RunCommandLineAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that runs a user-specified command line.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_RunCommandLineAction : SMS_TaskSequence_Action
{
      String CommandLine;
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean DisableWow64Redirection;
      Boolean Enabled;
      String Name;
      String PackageID;
      String OutputVariableName;
      Boolean RunAsUser;
      String SuccessCodes;
      String SupportedEnvironment;
      UInt32 Timeout;
      String UserName;
      String UserPassword;
      String WorkingDirectory;
};
```

## Methods

The `SMS_TaskSequence_RunCommandLineAction` class doesn't define any methods.

## Properties

### `CommandLine`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null, CommandLineArg(2), AllowedLen("1-32000")]`

Specify a command-line. The length can be between 1 and 32,000 characters. For example: `cmd /c ipconfig > c:\ipconfig.txt`

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

Qualifiers: `[AllowedLen("0-255")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `DisableWow64Redirection`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[Not_Null, VariableName("SMSTSDisableWow64Redirection")]`

Set `true` if the task sequence engine disables Wow64 file redirection and 64-bit registry redirection. It uses this behavior when it evaluates file, folder, and registry conditions on a 64-bit OS. The default value is `false`.

The task sequence variable associated with this property is [SMSTSDisableWow64Redirection](../../../osd/understand/task-sequence-variables#SMSTSDisableWow64Redirection).

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `PackageID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[TaskSequencePackage, CommandLineArg(1)]`

The ID of a package associated with the action.

### `OutputVariableName`

Data type: `String`

Access type: Read/write

Qualifiers: None

Specify a task sequence variable to store the output of the script.

### `RunAsUser`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[VariableName("_SMSTSRunCommandLineAsUser"), RequireR2]`

When set to `true`, the command line runs under the credentials specified by the `UserName` property. The default value is: `false`

### `SuccessCodes`

Data type: `String`

Access type: Read/Write

Qualifiers: `[SuccessCodes, Not_Null]`

Exit codes that indicate success. The default setting is `"0 3010"`.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `UserName`

Data type: `String`

Access type: Read/Write

Qualifiers: `[VariableName("SMSTSRunCommandLineUserName"]`

The user account to run the command line under when the `RunAsUser` property is set to `true`.

### `UserPassword`

Data type: `String`

Access type: Read/Write

Qualifiers: `[VariableName("SMSTSRunCommandLineUserPassword", Secret]`

Masked password associated with the user account that is used to run the command line when the `RunAsUser` property is set to `true`.

### `WorkingDirectory`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("0-255")]`

The directory from which to run the command line. Set this property to an absolute path or a relative path. The path length must be between 0 and 255 characters.

## Remarks

Class qualifiers for this class include:

```
[CommandLine("smsswd.exe /run:%1 %2"),

ActionCategory("General,1,1"),ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "RunCommandLineControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).