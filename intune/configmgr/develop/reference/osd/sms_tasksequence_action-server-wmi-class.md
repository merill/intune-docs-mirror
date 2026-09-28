---
layout: Conceptual
title: SMS_TaskSequence_Action Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class
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
description: Learn how to use SMS_TaskSequence_Action class which serves as the abstract base class for all task sequence actions in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 42c1218e-73c7-c324-5ff3-4d84f1e4fb35
document_version_independent_id: f5b14503-8cef-9a4d-b5b2-4a2cf45ffbe6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4d30fcb9-59d8-c88e-a348-afeeb9bd6f24
---

# SMS_TaskSequence_Action Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_Action` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as the abstract base class for all task sequence actions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_Action : SMS_TaskSequence_Step
{
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

The `SMS_TaskSequence_Action` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class).

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

See [SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class).

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

The environment required to run the task sequence action. Possible values are:

- WinPE
- FullOS
- WinPEandFullOS

    The default value is WinPEandFullOS.

    `Timeout` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    The user-specified timeout value, in seconds. If the step does not finish in the specified time period, the client execution engine explicitly terminates the step.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Configuration Manager supports a number of built-in action classes that are derived from `SMS_TaskSequence_Action` that represent operations available to the administrator in the Configuration Manager console. An example is [SMS_TaskSequence_ApplyDataImageAction Server WMI Class](sms_tasksequence_applydataimageaction-server-wmi-class).

    By using the Operating System Deployment task sequence object model, your application can create and use task sequences that use the built-in actions. For more information, see About Operating System Deployment Task Sequences.

    You also use this class to create a custom task sequence action. For more information, see About Configuration Manager Custom Actions

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).