---
layout: Conceptual
title: SMS_TaskSequence_OfflineEnableBitLockerAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_offlineenablebitlockeraction
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
description: The SMS_TaskSequence_OfflineEnableBitLockerAction WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that pre-provisions BitLocker for the OS drive.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 48b765da-9728-7edb-02f2-da9f4d43b31c
document_version_independent_id: e2be0240-7e8b-1448-4cba-9145aa61971b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_offlineenablebitlockeraction.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_offlineenablebitlockeraction
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_offlineenablebitlockeraction.md
cmProducts: []
platformId: 79af86dd-760b-63e2-2c00-21b1a8a63cee
---

# SMS_TaskSequence_OfflineEnableBitLockerAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_OfflineEnableBitLockerAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that pre-provisions BitLocker for the OS drive.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_OfflineEnableBitLockerAction : SMS_TaskSequence_Action
{
    Object Condition;
    Boolean ContinueOnError;
    String Description;
    UInt32 DestinationDisk;
    String DestinationLogicalDrive;
    UInt32 DestinationPartition;
    String DestinationVariable;
    Boolean Enabled;
    Boolean EncryptFullDisk;
    UInt32 EncryptMethod;
    String Name;
    Boolean SkipWhenTPMInvalid;
    String SupportedEnvironment;
    UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_OfflineEnableBitLockerAction` class doesn't define any methods.

## Properties

### `Condition`

Data type: `Object`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `ContinueOnError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Description`

Data type: `String`

Access type: Read/Write

Qualifiers: `[allowedlen]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `DestinationDisk`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: `[commandlinearg(1), valuerange("0-99")]`

Index of the disk for which to pre-provision BitLocker. The index can have a value of 1 through 99.

### `DestinationLogicalDrive`

Data type: `String`

Access type: Read/Write

Qualifiers: `[commandlinearg(3), valuemap {"C:","D:","E:","F:","G:","H:","I:","J:","K:","L:","M:","N:","O:","P:","Q:","R:","S:","T:","U:","V:","W:","X:","Y:","Z:"}]`

Logical drive letter of the volume to which to provision BitLocker. Possible values are A-Z.

### `DestinationPartition`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: `[commandlinearg(2), requiredifnotnull("DesinationDisk"), valuerange("1-99")]`

Index of the partition on the target disk specified by `DestinationDisk` to which to pre-provision BitLocker. The index can have a value of 1 through 99.

### `DestinationVariable`

Data type: `String`

Access type: Read/Write

Qualifiers: `[commandlinearg]`

Task sequence variable containing the logical drive letter of the volume to which to pre-provision BitLocker.

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `EncryptFullDisk`

Data type: `Boolean`

Access type: Read/write

Configure the step to use full disk encryption. The default value is `false`.

### `EncryptMethod`

Data type: `UInt32`

Access type: Read/write

Specify the disk encryption mode. Set `0` to not specify the mode, which is the default.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[allowedlen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `SkipWhenTPMInvalid`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[commandlinearg(5), not_null]`

Set `true` to skip this step for computers that don't have a TPM or when TPM isn't enabled.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[not_null, valuemap]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is `WinPE`.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

```
[CommandLine(     "OSDOfflineBitlocker.exe /enable \<?1: /disk:%1>\<?2: /part:%2>\<?3: /drive:%3>\<?4: /drive:%%%4%%>\<?5: /ignoretpm:%5>"     ),

ActionCategory{"Disks,6,3"},     ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "OfflineBitlockerControl", "TaskSequenceOptionControl"},     VariablePrefix("OSDBitLocker")     ]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

## Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).