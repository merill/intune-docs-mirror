---
layout: Conceptual
title: SMS_TaskSequence_CaptureSystemImageAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_capturesystemimageaction-server-wmi-class
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
description: The SMS_TaskSequence_CaptureSystemImageAction class represents a task sequence action that specifies an existing network share and WIM file to use when saving the image.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6e69e1df-8c18-edbe-bb65-7d86b40a4ea9
document_version_independent_id: b640012b-6794-50a8-ab2e-4eef852e4360
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_capturesystemimageaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_capturesystemimageaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_capturesystemimageaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bbcfe2ca-b641-8762-4bb3-e2e2aff6f2ab
---

# SMS_TaskSequence_CaptureSystemImageAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_CaptureSystemImageAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that specifies an existing network share and WIM file to use when saving the image.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_CaptureSystemImageAction : SMS_TaskSequence_Action
{
      String CaptureDestination;
      String CapturePassword;
      String CaptureUsername;
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String ImageCreator;
      String ImageDescription;
      String ImageVersion;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_CaptureSystemImageAction` class does not define any methods.

## Properties

`CaptureDestination` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, AllowedLen("1-255")]

The path where the captured image is saved. This path is overwritten if the file exists already. The path length can be between 1 and 255 characters. This property is required.

`CapturePassword` Data type: `String`

Access type: Read/Write

Qualifiers:

[VariableName("OSDCaptureAccountPassword"), Secret]

Password of the account specified by the `CaptureUsername` property.

The task sequence variable associated with this property is OSDCaptureAccountPassword. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDCaptureAccountPassword).

`CaptureUsername` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDCaptureAccount")]

A Windows account name that has permissions to the network share where the captured image will be stored, specified by `CaptureDestination`. This name is specified in "domain\username" format. To set this property, you must have write access to the destination folder.

The task sequence variable associated with this property is OSDCaptureAccount. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDCaptureAccount).

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

`ImageCreator` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

Name of the creator of the image. The creation information is stored in the image header. The name length can be between 0 and 255 characters.

`ImageDescription` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

Description of the image as supplied by the creator and stored in the image header. The description length can be between 0 and 255 characters.

`ImageVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, AllowedLen("0-32")]

Version of the image as supplied by the creator and stored in the image header. The version length can be between 0 and 32 characters. This property is required.

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

## Remarks

Class qualifiers for this class include:

[CommandLine("osdcapturesystemimage.exe"),VariablePrefix("OSD"),

ActionCategory{"Images,8,5"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "CaptureSystemImageControl", "TaskSequenceOptionControl"}, SequenceCategory("OSD")]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).