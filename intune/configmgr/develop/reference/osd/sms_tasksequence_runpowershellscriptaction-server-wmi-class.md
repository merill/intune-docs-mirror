---
layout: Conceptual
title: SMS_TaskSequence_RunPowerShellScriptAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_runpowershellscriptaction-server-wmi-class
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
description: The `SMS_TaskSequence_RunPowerShellScriptAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that runs a user-specified Windows PowerShell script.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e908f22d-0ce0-5aa9-55b1-e7abdd72a806
document_version_independent_id: 65307e0d-3836-8414-d84e-71959a78f9ec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_runpowershellscriptaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_runpowershellscriptaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_runpowershellscriptaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 079847dc-5e88-23e1-f931-6e9b6d14c1f2
---

# SMS_TaskSequence_RunPowerShellScriptAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_RunPowerShellScriptAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that runs a user-specified Windows PowerShell script.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_RunPowerShellScriptAction : SMS_TaskSequence_Action
{
    SMS_TaskSequence_Condition Condition;
    Boolean ContinueOnError;
    String Description;
    Boolean Enabled;
    string ExecutionPolicy;
    String Name;
    string OutputVariableName;
    string PackageID;
    string Parameters;
    boolean RunAsUser;
    string ScriptName;
    string SourceScript;
    string SuccessCodes;
    string SupportedEnvironment;
    UInt32 Timeout;
    string UserName;
    string UserPassword;
    string WorkingDirectory;
};
```

## Methods

The `SMS_TaskSequence_RunPowerShellScriptAction` class doesn't define any methods.

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

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `ExecutionPolicy`

Data type: `String`

Access type: Read/write

Qualifiers: `[ValueMap{"Restricted", "AllSigned", "RemoteSigned", "Unrestricted", "Bypass", "Undefined"}, Not_Null:ToInstance]`

Specify the PowerShell execution policy. By default the value is `Restricted`.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `OutputVariableName`

Data type: `String`

Access type: Read/write

Qualifiers: None

Specify a task sequence variable to store the output of the script.

### `PackageID`

Data type: `String`

Access type: Read/write

Qualifiers: `[RequiredIfNull("SourceScript"), TaskSequencePackage]`

The ID of a package that includes the script.

### `Parameters`

Data type: `String`

Access type: Read/write

Qualifiers: [Not\_Null]

Specify any parameters to pass on the PowerShell command line for the script.

### `RunAsUser`

Data type: `Boolean`

Access type: Read/write

Qualifiers: [VariableName("\_SMSTSRunPowerShellAsUser"), RequireR2]

When set to `true`, the command line runs under the credentials specified by the `UserName` property.

The default value is: `false`

### `ScriptName`

Data type: `String`

Access type: Read/write

Qualifiers: `[RequiredIfNull("SourceScript")]`

The name of the source PowerShell script.

### `SourceScript`

Data type: `String`

Access type: Read/write

Qualifiers: `[RequiredIfNull("PackageID")]`

Specify the package ID of the source script to import.

### `SuccessCodes`

Data type: `String`

Access type: `Read/Write`

Qualifiers: `[SuccessCodes, Not_Null]`

Exit codes that indicate success. The default value is `"0 3010"`.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

The default value is `WinPEandFullOS`.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `UserName`

Data type: `String`

Access type: Read/Write

Qualifiers: `[VariableName("SMSTSRunPowerShellUserName"]`

The user account to run the command line under when the `RunAsUser` property is set to `true`.

### `UserPassword`

Data type: `String`

Access type: Read/Write

Qualifiers: `[VariableName("SMSTSRunPowerShellUserPassword", Secret]`

Masked password associated with the user account that is used to run the command line when the `RunAsUser` property is set to `true`.

### `WorkingDirectory`

Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

The directory from which to run the command line. Set this property to an absolute path or a relative path. The path length must be between 0 and 255 characters.

## Remarks

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).