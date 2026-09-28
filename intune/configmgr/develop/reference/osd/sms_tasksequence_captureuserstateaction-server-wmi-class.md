---
layout: Conceptual
title: SMS_TaskSequence_CaptureUserStateAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_captureuserstateaction-server-wmi-class
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
description: Learn how to use the SMS_TaskSequence_CaptureUserStateAction class in Configuration Manager to set a task sequence action that uses the User State Migration Tool (USMT) to capture user state and settings from the target computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 882f8fc3-9747-65bd-c615-5b344e3d7cbe
document_version_independent_id: 9fc0959e-b0ec-1e14-8c40-adff0668b75b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_captureuserstateaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_captureuserstateaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_captureuserstateaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 609fdc83-a0ec-f01b-daf6-a0ed3e112cff
---

# SMS_TaskSequence_CaptureUserStateAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_CaptureUserStateAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that uses the User State Migration Tool (USMT) to capture user state and settings from the target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_CaptureUserStateAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      String ConfigFiles[];
      Boolean ContinueOnError;
      Boolean ContinueOnLockedFiles;
      String Description;
      Boolean Enabled;
      Boolean EnableVerboseLogging;
      String FileAccess;
      String Mode;
      String Name;
      Boolean OfflineUserState;
      Boolean SkipEncryptedFiles;
      String SupportedEnvironment;
      UInt32 Timeout;
      Boolean UseHardlinks;
      String UsmtPackageID;
};
```

## Methods

The `SMS_TaskSequence_CaptureUserStateAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ConfigFiles` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

The configuration files used to capture user profiles. Set this property for customized user profile migration.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ContinueOnLockedFiles` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [Not\_Null, VariableName("OSDMigrateContinueOnLockedFiles")]

`true` (default) to allow the capture user state action to proceed even if some files cannot be captured. This property is required.

The task sequence variable associated with this property is OSDMigrateContinueOnLockedFiles. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

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

`true` to enable verbose logging for the USMT. The default value is `false`. This property is required.

`FileAccess` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Corresponds to the UI option to **Copy by using file system access**.

- Normal (default)
- VSS

    `Mode` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null]

    Mode that allows customization of the files captured by the USMT. Possible values are:
- Simple (default)
- Advanced

    This property is required.

    `Name` Data type: `String`

    Access type: Read/Write

    Qualifiers: [AllowedLen("1-100")]

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    `OfflineUserState` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: [Not\_Null, VariableName("\_OSDMigrateOfflineUserState")]

    `true` to migrate offline user state. The default value is `false`.

    `SkipEncryptedFiles` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: [Not\_Null, VariableName("OSDMigrateSkipEncryptedFiles")]

    `true` to skip encrypted files. The default value is `false`.

    The task sequence variable associated with this property is OSDMigrateSkipEncryptedFiles. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

    `SupportedEnvironment` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null:ToInstance]

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    The default value of this property for this task sequence action is FullOS.

    `Timeout` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

    `UseHardlinks` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: [Not\_Null, VariableName("\_OSDMigrateUseHardlinks")]

    `true` to configure USMT to use hardlinks. The default value is `false`.

    `UsmtPackageID` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null, VariableName("\_OSDMigrateUsmtPackageID"), TaskSequencePackage]

    The ID of the Configuration Manager package that contains USMT binaries. This property is required.

    The task sequence variable associated with this property is \_OSDMigrateUsmtPackageID. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

## Remarks

Class qualifiers for this class include:

[CommandLine("osdmigrateuserstate.exe /collect /continueOnError:%%OSDMigrateContinueOnLockedFiles%% /skipefs:%%OSDMigrateSkipEncryptedFiles%%"),VariablePrefix("OSDMigrate"),

ActionCategory{"UserState,2,4"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "CaptureUserStateControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).