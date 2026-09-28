---
layout: Conceptual
title: SMS_TaskSequence_InstallUpdateAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_installupdateaction-server-wmi-class
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
description: An SMS Provider server class in configuration Manager. It represents a task sequence that installs software updates on a target computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 99f4d941-f74a-41c1-e069-de66d2860d41
document_version_independent_id: 9eda6f7b-ad73-63d7-166a-d8a5e7c95d89
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_installupdateaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_installupdateaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_installupdateaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9335e88f-d00c-e198-bf97-cc20b9eddd33
---

# SMS_TaskSequence_InstallUpdateAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_InstallUpdateAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that installs software updates on a target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_InstallUpdateAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Name;
      String RetryCount;
      String SupportedEnvironment;
      String Target;
      UInt32 Timeout;
      Boolean UseCache;
};
```

## Methods

The `SMS_TaskSequence_InstallUpdateAction` class does not define any methods.

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

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

[SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`RetryCount` Data type: `String`

Access type: Read/Write

Qualifiers: [retrycount]

The number of retries. The default value is 2.

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is FullOS.

`Target` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, VariableName("SMSInstallUpdateTarget")]

Designator for installing assigned software updates on the target computer. Possible values are:

- Mandatory. Install all software updates flagged in Configuration Manager as mandatory for the computers targeted by this task sequence action.
- All. Install all software updates for the computers targeted by this task sequence action.

    The task sequence variable associated with this property is SMSInstallUpdateTarget. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

    `Timeout` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    `UseCache` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: [not\_null, variablename("SMSTSSoftwareUpdateScanUseCache")]

    Indicates whether the cache is used. The default value is `true`.

## Remarks

Class qualifiers for this class include:

[CommandLine("TSInstallSWUpdate.exe /target:%%SMSInstallUpdateTarget%%"),

ActionCategory{"Software,3,2"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "InstallSoftwareUpdateControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).