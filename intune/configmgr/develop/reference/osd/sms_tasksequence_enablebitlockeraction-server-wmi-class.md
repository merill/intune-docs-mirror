---
layout: Conceptual
title: SMS_TaskSequence_EnableBitLockerAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_enablebitlockeraction-server-wmi-class
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
description: The SMS_TaskSequence_EnableBitLockerAction WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that enables the BitLocker encryption on the specified drive.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ef9b3512-70c8-6891-a3c5-53b82b3cff79
document_version_independent_id: cc0d4d3e-7d45-0440-b322-f6fbff5de7e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_enablebitlockeraction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_enablebitlockeraction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_enablebitlockeraction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 285a7a45-61ba-30bd-b5a0-d645d74009e1
---

# SMS_TaskSequence_EnableBitLockerAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_EnableBitLockerAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that enables the BitLocker encryption on the specified drive.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_EnableBitLockerAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String CreateRecoveryPassword;
      String Description;
      Boolean Enabled;
      UInt32 EncryptMethod;
      String Mode;
      String Name;
      String PIN;
      Boolean SkipWhenNoValidTPM;
      String StartupKeyDrive;
      String SupportedEnvironment;
      String TargetDrive;
      UInt32 Timeout;
      Boolean WaitForEncryption;
};
```

## Methods

The `SMS_TaskSequence_EnableBitLockerAction` class doesn't define any methods.

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

### `CreateRecoveryPassword`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(5), Not_Null]`

Indicates whether a recovery password should be created in Active Directory. Possible values are:

- `None`
- `AD` (default)

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

### `EncryptMethod`

Data type: `UInt32`

Access type: Read/write

Specify the disk encryption mode. Set `0` to not specify the mode, which is the default.

### `Mode`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(3), RequiredIfNull("TargetDrive")]`

Key protector mode. Possible values are:

- `TPM`
- `Key`
- `TPMAndKey`
- `TPMAndPIN`

The default value is `null`. This property is required if `TargetDrive` is set to `null`.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `PIN`

Data type: `String`

Access type: Read/Write

Qualifiers: `[VariableName("OSDBitLockerPIN"), Secret, AllowedLen("0-255")]`

The PIN for BitLocker encryption. Only valid if the **Mode** property is set to `"TPMAndPIN"`.

### `SkipWhenNoValidTPM`

Data type: `Boolean`

Access type: Read/write

Set `true` to skip this step for computers that don't have a TPM or when TPM isn't enabled. By default the value is `false`.

### `StartupKeyDrive`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(4)]`

Drive letter of removable USB drive on which to store key protectors. This property is ignored unless the **Mode** property is set to `Key` or `TPMAndKey`. Set this property to `null` (default) to use the first available USB drive.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is `FullOS`.

### `TargetDrive`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(1)]`

Drive letter of the volume on which to enable the BitLocker encryption. Set this property to `null` (default) to use the current OS volume.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `WaitForEncryption`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[CommandLineArg(2), Not_Null]`

Set `true` to wait for disk encryption to complete before continuing with the task sequence. Set this property to `false` (default) to continue the task sequence while encryption proceeds in the background.

## Remarks

Class qualifiers for this class include:

```
[CommandLine("OSDBitLocker.exe /enable \<?1: /drive:%1>\<?2: /wait:%2>\<?3: /mode:%3>\<?4: /keydrive:%4>\<?5: /pwd:%5>"),

ActionCategory{"Disks,4,3"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "EnableBitLockerControl", "TaskSequenceOptionControl"},

VariablePrefix("OSDBitLocker")]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

BitLocker requires at least two partitions on the hard drive. The first partition contains the Windows bootstrap code, and the second partition contains the OS. The bootstrap partition must remain unencrypted.

The variable prefix for this class is "OSDBitLocker".

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).