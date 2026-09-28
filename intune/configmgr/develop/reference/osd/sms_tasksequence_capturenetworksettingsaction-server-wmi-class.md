---
layout: Conceptual
title: SMS_TaskSequence_CaptureNetworkSettingsAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_capturenetworksettingsaction-server-wmi-class
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
description: Details of the SMS_TaskSequence_CaptureNetworkSettingsAction server WMI class
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8eca0225-8d91-f9d8-82b4-c8d0d840e4bc
document_version_independent_id: 4d4f4102-fd9c-4178-c01d-c0ee0cfd4f6e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_capturenetworksettingsaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_capturenetworksettingsaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_capturenetworksettingsaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d668fc94-9ec6-0ac2-fdf9-2f2bcee20c2b
---

# SMS_TaskSequence_CaptureNetworkSettingsAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_CaptureNetworkSettingsAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that captures network settings from the target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_CaptureNetworkSettingsAction : SMS_TaskSequence_Action
{
          SMS_TaskSequence_Condition Condition;
          Boolean ContinueOnError;
          String Description;
          Boolean Enabled;
          Boolean MigrateAdapterSettings;
          Boolean MigrateNetworkMembership;
          String Name;
          String SupportedEnvironment;
          UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_CaptureNetworkSettingsAction` class does not define any methods.

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

`MigrateAdapterSettings` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null, VariableName("OSDMigrateAdapterSettings")]

`true` (default) to migrate TCP/IP and DNS settings for network adapters.

The task sequence variable associated with this property is OSDMigrateAdapterSettings. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDMigrateAdapterSettings).

`MigrateNetworkMembership` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null, VariableName("OSDMigrateNetworkMembership")]

`true` to migrate workgroup or domain membership information as part of operating system deployment. The default value is `false`.

The task sequence variable associated with this property is OSDMigrateNetworkMembership. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDMigrateNetworkMembership).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

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

## Remarks

Class qualifiers for this class include:

[CommandLine("osdnetsettings.exe capture netmembership:%%OSDMigrateNetworkMembership%% adapters:%%OSDMigrateAdapterSettings%%"),

ActionCategory{"Settings,1,7"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "CaptureNetworkSettingsControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).