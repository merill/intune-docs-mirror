---
layout: Conceptual
title: SMS_TaskSequence_ApplyNetworkSettingsAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applynetworksettingsaction-server-wmi-class
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
description: Represent a task sequence action that specifies the network or workgroup configuration information for the target computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 552daf49-99c5-66e7-b9cf-6b441aceaf55
document_version_independent_id: 96408417-21e2-4663-943b-a07f692e8341
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_applynetworksettingsaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_applynetworksettingsaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_applynetworksettingsaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a856fde3-2f79-b9f7-f0ca-157c09f8e30b
---

# SMS_TaskSequence_ApplyNetworkSettingsAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ApplyNetworkSettingsAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that specifies the network or workgroup configuration information for the target computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_ApplyNetworkSettingsAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_NetworkAdapterSettings Adapters[];
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      String DNSDomain;
      String DNSSuffixSearchOrder[];
      String DomainName;
      String DomainOUName;
      String DomainPassword;
      String DomainUsername;
      Boolean Enabled;
      Boolean EnableTCPIPFiltering;
      String Name;
      UInt32 NetworkJoinType;
      UInt32 NumAdapters;
      String SupportedEnvironment;
      UInt32 Timeout;
      String WorkgroupName;
};
```

## Methods

The `SMS_TaskSequence_ApplyNetworkSettingsAction` class does not define any methods.

## Properties

`Adapters` Data type: `SMS_TaskSequence_NetworkAdapterSettings` Array

Access type: Read/Write

Qualifiers: [Global, VariableName("OSDAdapter")]

[SMS_TaskSequence_NetworkAdapterSettings Server WMI Class](sms_tasksequence_networkadaptersettings-server-wmi-class) objects representing settings for the adapters installed on the target computer. This property must be global so that it is visible in finalize mode.

The task sequence variable associated with this property is OSDAdapter. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDAdapter).

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

`DNSDomain` Data type: `String`

Access type: Read/Write

Qualifiers: [Global]

The primary Domain Name System (DNS) domain. This property must be global so that it is visible in finalize mode.

`DNSSuffixSearchOrder` Data type: `String` Array

Access type: Read/Write

Qualifiers: [Global]

The DNS suffix search order. This property must be global so that it is visible in finalize mode.

`DomainName` Data type: `String`

Access type: Read/Write

Qualifiers: [RequiredIfNull("WorkgroupName"), AllowedLen("1-255")]

Name of the domain for the target computer. The name can be between 1 and 255 characters in length. Supply this name if `NetworkJoinType` is set to 0.

`DomainOUName` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-32767")]

The name of the Active Directory organizational unit (OU) to which the user belongs. The name can be between 0 and 32,767 characters in length. Set this property if `NetworkJoinType` is set to 0.

`DomainPassword` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDJoinPassword"), Secret]

Password of the account used when the user joins a Windows domain. Set this property if `NetworkJoinType` is set to 0.

The task sequence variable associated with this property is OSDJoinPassword. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDJoinPassword).

`DomainUsername` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDJoinAccount")]

Account used when the user joins a Windows domain. Set this property if `NetworkJoinType` is set to 0.

The task sequence variable associated with this property is OSDJoinAccount, which specifies the network account that should be used to add the target computer to a Windows domain. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDJoinAccount).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`EnableTCPIPFiltering` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [Global]

`true` to enable TCP/IP filtering. The default value is `false`. This property must be global so that it is visible in finalize mode.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`NetworkJoinType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Not\_Null]

The type of network join supported by the target computer. Possible values are:

| Value | Network join type |
| --- | --- |
| 0 | Domain |
| 1 | Workgroup |

`NumAdapters` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Global, VariableName("OSDAdapterCount")]

Size of the array indicated by the `Adapters` property. This property must be global so that it is visible in finalize mode.

The task sequence variable associated with this property is OSDAdapterCount. For more information, see [OS deployment task sequence variables](../../../osd/understand/task-sequence-variables#OSDAdapterCount).

OSDAdapterCount

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`WorkgroupName` Data type: `String`

Access type: Read/Write

Qualifiers: [RequiredIfNull("DomainName"), AllowedLen("1-32")]

Name of the workgroup joined by the target computer. The name can be between 1 and 32 characters in length. Set this property if `NetworkJoinType` is set to 1.

## Remarks

Class qualifiers for this class include:

[CommandLine("osdnetsettings.exe configure"),VariablePrefix("OSD"), ActionCategory{"Settings,3,7"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ApplyNetworkSettingsControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).