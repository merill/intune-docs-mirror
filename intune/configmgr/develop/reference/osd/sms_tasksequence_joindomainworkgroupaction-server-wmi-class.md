---
layout: Conceptual
title: SMS_TaskSequence_JoinDomainWorkgroupAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_joindomainworkgroupaction-server-wmi-class
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
description: The SMS_TaskSequence_JoinDomainWorkgroupAction WMI class is an SMS Provider server class that represents a task sequence action that joins a Windows domain or a Windows workgroup.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 060eebd9-9590-6ff3-164c-e564c9c7cb11
document_version_independent_id: 6f6b5db8-9165-146d-ef24-abff07970621
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_joindomainworkgroupaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_joindomainworkgroupaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_joindomainworkgroupaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e3da6357-d216-e332-5a7b-e7ca6746307c
---

# SMS_TaskSequence_JoinDomainWorkgroupAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_JoinDomainWorkgroupAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that joins a Windows domain or a Windows workgroup.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_JoinDomainWorkgroupAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      String DomainName;
      String DomainOUName;
      String DomainPassword;
      String DomainUsername;
      Boolean Enabled;
      String Name;
      Boolean SkipReboot;
      String SupportedEnvironment;
      UInt32 Timeout;
      UInt32 Type;
      String WorkgroupName;
};
```

## Methods

The `SMS_TaskSequence_JoinDomainWorkgroupAction` class does not define any methods.

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

`DomainName` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-255")]

Name of the domain for the target computer. The name length can be between 1 and 255 characters. Set this property if the `Type` property is set to 0.

`DomainOUName` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-32767")]

The name of the Active Directory organizational unit (OU) to join. The name length can be between 0 and 32767 characters. Set this property if the `Type` property is set to 0.

`DomainPassword` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDJoinPassword"), Secret]

Password of the account specified by `DomainUsername`. Set this property if the `Type` property is set to 0.

The task sequence variable associated with this property is OSDJoinPassword. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`DomainPassword` might be required to disjoin from the computer's domain.

`DomainUsername` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDJoinAccount")]

Account that should be used by the target computer to join a Windows domain, with appropriate domain join rights. Set this property if the `Type` property is set to 0.

The task sequence variable associated with this property is OSDJoinAccount. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`DomainUserName` may be required to disjoin from the computer's domain.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`SkipReboot` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` to skip reboot after the network join action is complete.

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

The default value of this property for this task sequence action is FullOS.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, VariableName("OSDJoinType")]

The type of network join action required of the target computer. Possible values are:

| Value | Network join type |
| --- | --- |
| 0 | Domain |
| 1 | Workgroup |

The task sequence variable associated with this property is OSDJoinType. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables).

`WorkgroupName` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-32")]

Name of the workgroup to join. The name length can be between 1 and 32 characters. Set this property if the `Type` property is set to 1.

## Remarks

Class qualifiers for this class include:

[CommandLine("osdjoin.exe /type:%%OSDJoinType%%"), VariablePrefix("OSDJoin"),

ActionCategory{"General,4,1"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "JoinDomainControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).