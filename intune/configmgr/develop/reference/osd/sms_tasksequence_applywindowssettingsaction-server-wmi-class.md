---
layout: Conceptual
title: SMS_TaskSequence_ApplyWindowsSettingsAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applywindowssettingsaction-server-wmi-class
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
description: The SMS_TaskSequence_ApplyWindowsSettingsAction WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that applies Windows settings configuration information for the target computer.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b9da4fc7-58d9-4841-8a14-e037b62b665c
document_version_independent_id: 574f81a7-63b1-102f-2ee1-bae18687eeb2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_applywindowssettingsaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_applywindowssettingsaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_applywindowssettingsaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c062a8ea-9ef9-8aac-4e01-4c2ed39b364b
---

# SMS_TaskSequence_ApplyWindowsSettingsAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ApplyWindowsSettingsAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that applies Windows settings configuration information for the target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_ApplyWindowsSettingsAction : SMS_TaskSequence_Action
{
    String AdminPassword;
    String ComputerName;
    SMS_TaskSequence_Condition Condition;
    Boolean ContinueOnError;
    String Description;
    Boolean Enabled;
    String InputLocale;
    String Name;
    String ProductKey;
    Boolean RandomAdminPassword;
    String RegisteredOrgName;
    String RegisteredUserName;
    UInt32 ServerLicenseConnectionLimit;
    String ServerLicenseMode;
    String SystemLocale;
    String SupportedEnvironment;
    UInt32 Timeout;
    String TimeZone;
    string UILanguage;
    string UILanguageFallback;
    string UserLocale;

};
```

## Methods

The `SMS_TaskSequence_ApplyWindowsSettingsAction` class doesn't define any methods.

## Properties

### `AdminPassword`

Data type: `String`

Access type: Read/Write

Qualifiers: `[VariableName("OSDLocalAdminPassword"), Secret, AllowedLen("0-255")]`

The local Administrator password. The name can be between 0 and 255 characters in length. This property must be set, but it's ignored if the `RandomAdminPassword` property is set to `true`.

The task sequence variable associated with this property is [OSDLocalAdminPassword](../../../osd/understand/task-sequence-variables#OSDLocalAdminPassword).

### `ComputerName`

Data type: `String`

Access type: Read/Write

Qualifiers: None

Name assigned to the target computer. The default value is `"%_SMSTSMachineName%"`.

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

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `InputLocale`

Data type: `String`

Access type: Read/write

Specify the default keyboard layout. For more information on this Windows setup answer file value, see [Microsoft-Windows-International-Core](/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-international-core).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `ProductKey`

Data type: `String`

Access type: Read/Write

Qualifiers: `[QuasiSecret]`

The product code for the new OS.

### `RandomAdminPassword`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[not_null]`

- Set `true` (default) to set the Administrator password to a randomly generated value. It also disables the account in the new OS.
- Set `false` to enable the local Administrator account. It also sets the password as specified by the `AdminPassword` property.

This property is required.

### `RegisteredOrgName`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null, AllowedLen("1-255")]`

Registered organization name in the new OS. The name length can be between 1 and 255 characters. This property is required.

### `RegisteredUserName`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null, AllowedLen("1-255")]`

Registered user name in the new OS. The name length can be between 1 and 255 characters. This property is required.

### `ServerLicenseConnectionLimit`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: `[ValueRange("5-9999")]`

Limit on server license connections. The value can be between 5 and 9999. Use this property to configure server licensing on Windows Server.

### `ServerLicenseMode`

Data type: `String`

Access type: Read/Write

Qualifiers: None

The server licensing mode. Possible values for Windows Server are:

- `PerSeat`
- `PerServer`

### `SystemLocale`

Data type: `String`

Access type: Read/write

Specify system locale. For more information on this Windows setup answer file value, see [Microsoft-Windows-International-Core](/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-international-core).

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is WinPE.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `TimeZone`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null]`

Time zone for the new OS. Set this property to an English language string. A non-English localized string causes the time zone setting to fail and default to Universal Coordinated Time (UTC).

### `UILanguage`

Data type: `String`

Access type: Read/write

Specify the Windows UI language. For more information on this Windows setup answer file value, see [Microsoft-Windows-International-Core](/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-international-core).

### `UILanguageFallback`

Data type: `String`

Access type: Read/write

Specify the fallback language for the Windows UI. For more information on this Windows setup answer file value, see [Microsoft-Windows-International-Core](/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-international-core).

### `UserLocale`

Data type: `String`

Access type: Read/write

Specify the user locale. For more information on this Windows setup answer file value, see [Microsoft-Windows-International-Core](/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-international-core).

## Remarks

Class qualifiers for this class include:

```
[CommandLine("osdwinsettings.exe /config"),VariablePrefix("OSD"),

ActionCategory{"Settings,4,7"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ApplyWindowsSettingsControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).