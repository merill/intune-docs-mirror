---
layout: Conceptual
title: SMS_TaskSequence_AutoApplyAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_autoapplyaction-server-wmi-class
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
description: The SMS_TaskSequence_AutoApplyAction WMI class represents a task sequence action that matches and installs device drivers as part of an operating system deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6a1694e9-f467-0bc3-494e-03fe2f344f6c
document_version_independent_id: 32877e40-8319-dd15-3ec1-7e17fff22449
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_autoapplyaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_autoapplyaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_autoapplyaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 027ec034-9065-9c6e-7ac0-c558e9fee0c9
---

# SMS_TaskSequence_AutoApplyAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_AutoApplyAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that matches and installs device drivers as part of an operating system deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_AutoApplyAction : SMS_TaskSequence_Action
{
      Boolean BestMatch;
      String CategoryList[];
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      Boolean UnsignedDriver;
};
```

## Methods

The `SMS_TaskSequence_AutoApplyAction` class does not define any methods.

## Properties

`BestMatch` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [Not\_Null]

`true` (default) to install the device driver that is the best match for the hardware device. Set this property to `false` to install all compatible device drivers and have the operating system choose the best driver to use.

Note

This property is required by the task sequence action if there are multiple device drivers in the driver catalog that are compatible with the hardware device.

`CategoryList` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Unique IDs of categories for which the task sequence action searches in the driver catalog. The default value is `null`.

You can obtain the available category IDs by enumerating the SMS\_CategoryInstance Server WMI Class objects on the site.

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

`UnsignedDriver` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [Not\_Null, VariableName("OSDAllowUnsignedDriver")]

`true` to configure the Windows operating system to allow unsigned device drivers to be installed. The default value is `false`.

Note

This property is required by the action. However, it's deprecated and not used by modern OS versions.

## Remarks

Class qualifiers for this class include:

[CommandLine("osddriverclient.exe /auto /bestmatch:%%OSDAutoApplyDriverBestMatch%% /unsigned:%%OSDAllowUnsignedDriver%%"),

ActionCategory{"Drivers,1,6"},VariablePrefix("OSDAutoApplyDriver"),

ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "AutoApplyDriverControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).