---
layout: Conceptual
title: SMS_TaskSequence_SetupWindowsAndSMSAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_setupwindowsandsmsaction-server-wmi-class
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
description: Learn how to use Configuration Manager SMS_TaskSequence_SetupWindowsAndSMSAction Windows Management Instrumentation (WMI) class to represent a task sequence action that specifies the additional installation properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 87db49ec-397d-fac7-5dfb-c357a3ab129f
document_version_independent_id: 102a1652-ab18-7cd7-02b4-e7f5fae44cbf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_setupwindowsandsmsaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_setupwindowsandsmsaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_setupwindowsandsmsaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2fd25eef-12bc-7a1b-e4fb-bdb95ab5d8b6
---

# SMS_TaskSequence_SetupWindowsAndSMSAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_SetupWindowsAndSMSAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that specifies the additional installation properties that should be used when installing the Configuration Manager client.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_SetupWindowsAndSMSAction : SMS_TaskSequence_Action
{
      String ClientInstallProperties;
      String ClientPackageID;
      String ClientPreProductionPackageID;
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_SetupWindowsAndSMSAction` class does not define any methods.

## Properties

`ClientInstallProperties` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("SMSClientInstallProperties")]

List of Windows Installer properties to use when installing the Configuration Manager client.

The task sequence variable associated with this property is SMSClientInstallProperties. For more information, see [How to Set an Operating System Deployment Task Sequence Variable](../../osd/how-to-set-an-operating-system-deployment-task-sequence-variable).

`ClientPackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, TaskSequencePackage, VariableName("\_SMSClientPackageID")]

ID of the package containing the Configuration Manager client.

The task sequence variable associated with this property is \_SMSClientPackageID. For more information, see [How to Set an Operating System Deployment Task Sequence Variable](../../osd/how-to-set-an-operating-system-deployment-task-sequence-variable).

`ClientPreProductionPackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [TaskSequencePackage, VariableName("\_SMSClientPreProductionPackageID")]

ID of the pre-production package containing the Configuration Manager client. The default value is `null`.

The task sequence variable associated with this property is \_SMSClientPreProductionPackageID. For more information, see [How to Set an Operating System Deployment Task Sequence Variable](../../osd/how-to-set-an-operating-system-deployment-task-sequence-variable).

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

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

## Remarks

Class qualifiers for this class include:

[CommandLine("OSDSetupWindows.exe"),

ActionCategory{"Images,3,5"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "SetupWindowsAndSmsControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).