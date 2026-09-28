---
layout: Conceptual
title: SMS_TaskSequence_ApplyDataImageAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applydataimageaction-server-wmi-class
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
description: An SMS Provider server class that represents a task sequence action to apply an existing data image to a target computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 13ebdee7-a0d8-a24b-c38a-dd37f22f1457
document_version_independent_id: cd450d8e-134f-119c-0846-41856b809d91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_applydataimageaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_applydataimageaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_applydataimageaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 76095fe7-6214-772a-f39a-b658dede1d99
---

# SMS_TaskSequence_ApplyDataImageAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ApplyDataImageAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that applies an existing data image to a target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ApplyDataImageAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      UInt32 DestinationDisk;
      String DestinationLogicalDrive;
      UInt32 DestinationPartition;
      String DestinationVariable;
      Boolean Enabled;
      UInt32 ImageIndex;
      String ImagePackageID;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      Boolean WipeDestinationPartition;
};
```

## Methods

The `SMS_TaskSequence_ApplyDataImageAction` class does not define any methods.

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

`DestinationDisk` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [CommandLineArg(6), ValueRange("0-99")]

Index of the disk to which to apply the image. The index can have a value of 1 through 99. For more information, see Remarks.

`DestinationLogicalDrive` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(8)]

Logical drive letter of the volume to which the image is applied. For more information, see Remarks.

`DestinationPartition` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [CommandLineArg(7), RequiredIfNotNull("DestinationDisk"), ValueRange("1-99")]

Index of the partition on the target disk specified by `DestinationDisk` to which the image is applied. The index can have a value of 1 through 99. For more information, see Remarks.

`DestinationVariable` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(9)]

Task sequence variable containing the logical drive letter of the volume to which the image is applied. For more information, see the Remarks section later in this topic.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ImageIndex` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Not\_Null, ValueRange("1-2147483647"), VariableName("OSDDataImageIndex")]

Index of the image in the WIM file applied to the target computer. Possible index values are 1 through 2147483647. For more information, see the note in Remarks.

The task sequence variable associated with this property is OSDDataImageIndex. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDDataImageIndex).

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, CommandLineArg(1), TaskSequencePackage("image")]

Package ID of the image applied to the target computer. For more information, see [SMS_ImagePackage Server WMI Class](sms_imagepackage-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is WinPE.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`WipeDestinationPartition` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null, VariableName("OSDWipeDestinationPartition")]

`true` (default) to wipe the contents of the destination partition before the image is applied.

The task sequence variable associated with this property is OSDWipeDestinationPartition. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDWipeDestinationPartition).

## Remarks

Class qualifiers for this class include:

[CommandLine("OSDApplyOS.exe /data:%1,%%OSDDataImageIndex%% &lt;?6: /target:%6,%7&gt;&lt;?8: /target:%8&gt;&lt;?9: /target:%%%9%%&gt;"), ActionCategory{"Images,2,5"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ApplyDataImageControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

The following properties can be set for the target of this task sequence action:

- `DestinationDisk`
- `DestinationPartition`
- `DestinationLogicalDrive`
- `DestinationVariable`

    To install to a specific disk or partition, set `DestinationDisk` and `DestinationPartition` and set the other destination properties to `null`.

    To install to a logical volume, such as c:\, set `DestinationLogicalDrive` and set the other properties to `null`.

    `DestinationVariable` can be set to a task sequence variable that contains the destination in the form of "1,1" to target disk 1, partition 1, or contains "c:" to target a logical volume.

    Set all the destination properties to `null` to use the "next available" formatted volume as the target.

Note

The value supplied for the `ImageIndex` property can be problematic if your application must range-check the property against a maximum value that is greater than 0x7fffffff (2147483647). In this case, your application cannot use the range qualifier on the property.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).