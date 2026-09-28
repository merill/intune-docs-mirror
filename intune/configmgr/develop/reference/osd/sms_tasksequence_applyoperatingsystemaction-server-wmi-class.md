---
layout: Conceptual
title: SMS_TaskSequence_ApplyOperatingSystemAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applyoperatingsystemaction-server-wmi-class
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
description: An SMS Provider server class that represents a task sequence action. It installs a specified operating system image on a target computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 54c58ffc-e06a-b10c-d4fa-dff81e426210
document_version_independent_id: c06b7337-5b41-af1e-8bcc-cb7f4a847292
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_applyoperatingsystemaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_applyoperatingsystemaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_applyoperatingsystemaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 8607cd86-73c4-79b9-5430-5669c95a04ca
---

# SMS_TaskSequence_ApplyOperatingSystemAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ApplyOperatingSystemAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that installs a specified operating system image on a target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ApplyOperatingSystemAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      String ConfigFileName;
      String ConfigFilePackage;
      Boolean ContinueOnError;
      String Description;
      UInt32 DestinationDisk;
      String DestinationLogicalDrive;
      UInt32 DestinationPartition;
      String DestinationVariable;
      Boolean Enabled;
      UInt32 ImageIndex;
      String ImagePackageID;
      UInt32 InstallEditionIndex;
      String InstallPackageID;
      String Name;
      Boolean RunFromNet;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_ApplyOperatingSystemAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ConfigFileName` Data type: `String`

Access type: Read/Write

Qualifiers: [RequiredIfNotNull("ConfigFilePackage"), VariableName("OSDConfigFileName")]

The name of the answer file specified in the `ConfigFilePackage` property. For more information, see the Remarks section later in this topic.

The task sequence variable associated with this property is OSDConfigFileName. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDConfigFileName).

`ConfigFilePackage` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(4), TaskSequencePackage]

ID of the optional package containing the Windows setup answer file. For more information, see the Remarks section later in this topic.

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

Index of the disk to which to apply the image. The index can have a value of 0 through 99. For more information, see the Remarks section later in this topic.

`DestinationLogicalDrive` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(8)]

Logical drive letter of the volume to which the image is applied. For more information, see the Remarks section later in this topic.

`DestinationPartition` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [CommandLineArg(7), RequiredIfNotNull("DestinationDisk"), ValueRange("1-99")]

Index of the partition on the target disk specified by `DestinationDisk` to which the image is applied. The index can have a value of 1 through 99. For more information, see the Remarks section later in this topic.

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

Qualifiers: [RequiredIfNotNull("ImagePackageID"), ValueRange("1-2147483647"), VariableName("OSDImageIndex")]

Index of the image in the WIM file applied to the target computer. The value of this property can be between 1 and 2147483647. This property is required if `ImagePackageID` is set. For more information, see the Remarks section later in this topic.

The task sequence variable associated with this property is OSDImageIndex. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDImageIndex).

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(1), TaskSequencePackage("image"),RequiredIfNull("InstallPackageID")]

Package ID of the image applied to the target computer. This property is required if `InstallPackageID` is not set. For more information, see the Remarks section later in this topic.

`InstallEditionIndex` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [RequiredIfNotNull("InstallPackageID"), VariableName("OSDInstallEditionIndex")]

The edition index for a scripted installation, reflected in the WIM file applied to the target computer. The default value is 0. This property is required if `InstallPackageID` is set. For more information, see the Remarks section later in this topic.

`InstallPackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(3), TaskSequencePackage("image"), RequiredIfNull("ImagePackageID")]

Package ID of the scripted operating system install package to install on the target computer. For more information, see the Remarks section later in this topic.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`RunFromNet` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [RunFromNet, CommandLineArg(10)]

`true` if the operating system WIM image will be applied directly from a network share instead of being downloaded first. This requires that the image package be made available on a share on the distribution point. The default value is `false`.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is WinPE.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

[CommandLine("OSDApplyOS.exe&lt;?1: /image:%1,%%OSDImageIndex%%&gt;&lt;?3: /install:%3,%%OSDInstallEditionIndex%%&gt;&lt;?4: \"/config:%4,%%OSDConfigFileName%%\"&gt;&lt;?6: /target:%6,%7&gt;&lt;?8: /target:%8&gt;&lt;?9: /target:%%%9%%&gt;"),

ActionCategory{"Images,1,5"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ApplyOperatingSystemControl","TaskSequenceOptionControl"},SequenceCategory("OSD")]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

The following properties can be set for the target of this task sequence action:

- `DestinationDisk`
- `DestinationPartition`
- `DestinationLogicalDrive`
- `DestinationVariable`

    To install to a specific disk or partition, set `DestinationDisk` and `DestinationPartition` and set the other destination properties to `null`.

    To install to a logical volume, such as c:\, set `DestinationLogicalDrive` and set the other properties to `null`.

    `DestinationVariable` can be set to a task sequence variable that contains the destination in the form of "1,1" to target disk 1, partition 1, or contains "c:" to target a logical volume.

    Set all the destination properties to `null`, to use the "next available" formatted volume as the target.

    The following properties are specific to a particular type of installation:
- The `ImagePackageID` and `ImageIndex` properties are used for an image-based installation.
- The `InstallPackageID` and `InstallEditionIndex` properties are used for a scripted installation.
- The `ConfigFilePackage` and `ConfigFileName` properties are used for installation from a configuration file.

    The `InstallEditionIndex` property is set by the `SMS_TaskSequence_ApplyOperatingSystemAction` class. It is retrieved by [SMS_TaskSequence_SetupWindowsAndSMSAction Server WMI Class](sms_tasksequence_setupwindowsandsmsaction-server-wmi-class).

Note

The value supplied for the `ImageIndex` property can be problematic if your application has to range-check the property against a maximum value that is greater than 0x7fffffff (2147483647). In this case, your application cannot use the range qualifier on the property.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).