---
layout: Conceptual
title: SMS_TaskSequence_PartitionDiskAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_partitiondiskaction-server-wmi-class
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
description: The SMS_TaskSequence_PartitionDiskAction WMI class is an SMS Provider server class in Configuration Manager.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7b1c3ff7-a6bd-46e7-52db-9dc7326dd9cf
document_version_independent_id: b108b5b1-5cd4-adf0-3592-310fd150d1c4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_partitiondiskaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_partitiondiskaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_partitiondiskaction-server-wmi-class.md
cmProducts: []
platformId: e07ac222-8dc9-2449-32da-db802f941635
---

# SMS_TaskSequence_PartitionDiskAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_PartitionDiskAction` WMI class is an SMS Provider server class in Configuration Manager. It represents a task sequence action that formats and partitions a specified disk on a target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_PartitionDiskAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      UInt32 DiskIndex;
      String DiskIndexVariable;
      Boolean DiskpartBiosCompatibilityMode;
      String DiskType;
      Boolean Enabled;
      Boolean GPTBootDisk;
      String Name;
      SMS_TaskSequence_PartitionSettings Partitions[];
      String PartitionStyle;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_PartitionDiskAction` class doesn't define any methods.

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

Qualifiers: `[AllowedLen("0-255")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `DiskIndex`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: `[Not_Null]`

The number of the physical disk to partition and format.

### `DiskIndexVariable`

Data type: `String`

Access type: Read/write

Use a task sequence variable to specify the disk to format and partition.

### `DiskpartBiosCompatibilityMode`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Set `true` to disable sector alignment when partitioning the disk for compatibility with the target computer BIOS. The default value is `false`.

### `DiskType`

Data type: `String`

Access type: Read/Write

Qualifiers: None

Deprecated, don't use.

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `GPTBootDisk`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Set `true` to create an extensible firmware interface (EFI) partition so that an EFI system can boot from the disk. The default value is `false`. Set this property if `PartitionStyle` is set to GPT.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Partitions`

Data type: `SMS_TaskSequence_PartitionSettings` array

Access type: Read/Write

Qualifiers: `[Not_null]`

For more information on the objects representing partition settings, see [SMS_TaskSequence_PartitionSettings server WMI class](sms_tasksequence_partitionsettings-server-wmi-class).

### `PartitionStyle`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_null]`

The partition style. Possible values are:

- `GPT`: GUID partition table format.
- `MBR`: Master boot record format.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is `WinPE`.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

```
[CommandLine("osddiskpart.exe"),VariablePrefix("OSD"),

ActionCategory{"Disks,1,3"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "PartitionDiskControl", "TaskSequenceOptionControl"}]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).