---
layout: Conceptual
title: SMS_TaskSequence_RequestStateStoreAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_requeststatestoreaction-server-wmi-class
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
description: The SMS_TaskSequence_RequestStateStoreAction class represents a task sequence action that requests access to a state migration point when capturing a state from a computer or restoring a state to a computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 212e3885-5e1a-04f3-14f7-112aa5903d90
document_version_independent_id: 36e5f354-4717-8645-0bea-b2d83d9e8934
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_requeststatestoreaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_requeststatestoreaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_requeststatestoreaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9b30e60b-33e7-6fd5-ba99-df2ae21662c6
---

# SMS_TaskSequence_RequestStateStoreAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_RequestStateStoreAction` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence action that requests access to a state migration point when capturing a state from a computer or restoring a state to a computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_RequestStateStoreAction : SMS_TaskSequence_Action
{
      SMS_TaskSequence_Condition Condition;
      Boolean ContinueOnError;
      String Description;
      Boolean Enabled;
      Boolean FallbackToNAA;
      String Name;
      String RequestType;
      UInt32 SMPRetryCount;
      UInt32 SMPRetryTime;
      String SupportedEnvironment;
      UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_RequestStateStoreAction` class does not define any methods.

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

`FallbackToNAA` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the action should use the network access account (NAA) as a fallback when the computer account fails to connect to the state migration point. The default value is `false`.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`RequestType` Data type: `String`

Access type: Read/Write

Qualifiers: [CommandLineArg(1), Not\_Null]

Type of state migration point (SMP) request. Possible values are:

- capture
- restore

    `SMPRetryCount` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [Global, ValueRange("0-30")]

    The number of times that the action should try to find a state migration point before failing (global setting). The value must be between 0 and 30.

    `SMPRetryTime` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [Global, ValueRange("0-600")]

    The time, in seconds, that the action should wait between retry attempts (global setting).The value must be between 0 and 600.

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

[CommandLine("osdsmpclient.exe /%1"),VariablePrefix("OSDState"),

ActionCategory("UserState,1,4"),ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "RequestStateStoreControl", "TaskSequenceOptionControl"}]

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).