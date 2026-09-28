---
layout: Conceptual
title: SMS_TaskSequence_RestoreUserStateAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_restoreuserstateaction-server-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn about the simplified syntax, methods, properties, and requirements of the SMS_TaskSequence_RestoreUserStateAction server class.
locale: en-us
document_id: 8568df48-2fdd-3406-981d-5bee2e3141e6
document_version_independent_id: 34e8c72f-2efb-5f48-cf92-80ca39c98a4f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_restoreuserstateaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_restoreuserstateaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_restoreuserstateaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9c205434-0f15-3043-2db6-08ff4f1aee4b
---

# SMS_TaskSequence_RestoreUserStateAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_RestoreUserStateAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that initiates the User State Migration Tool (USMT) to restore user state and settings to a target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_RestoreUserStateAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      String ConfigFiles[];
      Boolean ContinueOnError;
      Boolean ContinueOnRestore;
      String Description;
      Boolean Enabled;
      Boolean EnableVerboseLogging;
      String LocalAccountPassword;
      Boolean LocalAccounts;
      String Mode;
      String Name;
      String SupportedEnvironment;
      UInt32 Timeout;
      String UsmtRestorePackageID;
};
```

## Methods

The `SMS_TaskSequence_RestoreUserStateAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ConfigFiles` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Configuration files used to capture user profiles. Set this property for customized user profile migration.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ContinueOnRestore` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null, VariableName("OSDMigrateContinueOnRestore")]

`true` (default) if user state restoration should continue even if some files cannot be restored.

The task sequence variable associated with this property is OSDMigrateContinueOnRestore. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`EnableVerboseLogging` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [Not\_Null]

`true` to enable USMT verbose logging. The default value is `false`.

`LocalAccountPassword` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDMigrateLocalAccountPassword"), Secret]

Password for the local user account to reset for restored local user profiles.

The task sequence variable associated with this property is OSDMigrateLocalAccountPassword. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`LocalAccounts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [VariableName("OSDMigrateLocalAccounts"), Not\_Null]

`true` to restore the local computer account. The default value is `false`.

The task sequence variable associated with this property is OSDMigrateLocalAccounts. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`Mode` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Mode for customizing the USMT file list. Possible values are shown below. The default value is Simple.

- Simple
- Advanced

    `Name` Data type: `String`

    Access type: Read/Write

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    `SupportedEnvironment` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null:ToInstance]

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    The default value of this property for this task sequence action is FullOS.

    `Timeout` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    `UsmtRestorePackageID` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null, TaskSequencePackage, VariableName("\_OSDMigrateUsmtRestorePackageID")]

    ID of the task sequence package containing the USMT program.

    The task sequence variable associated with this property is \_OSDMigrateUsmtRestorePackageID. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

## Remarks

Class qualifiers for this class include:

[CommandLine("osdmigrateuserstate.exe /apply /continueOnError:%%OSDMigrateContinueOnRestore%%"),

VariablePrefix("OSDMigrate"),

ActionCategory{"UserState,3,4"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "RestoreUserStateControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).