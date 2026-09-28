---
layout: Conceptual
title: SMS_TaskSequence Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class
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
description: Learn how to represent an operating system deployment task sequence using SMS_TaskSequence class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 145024f1-7bf7-aa37-5f0b-c3d9d4e9a8e4
document_version_independent_id: 40f264e2-ec84-27cc-a4ab-3f29df86f577
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: fbc980e2-d553-805d-e67f-8d59545dadf6
---

# SMS_TaskSequence Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an operating system deployment task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence
{
      String SchemaVersion;
      SMS_TaskSequence_Step Steps[];
};
```

## Methods

The following table shows the methods in `SMS_TaskSequence`.

| Method | Description |
| --- | --- |
| [ExportXml Method in Class SMS_TaskSequence](exportxml-method-in-class-sms_tasksequence) | Exports task sequence XML in a format that is suitable to use on another site. |
| [LoadFromXml Method in Class SMS_TaskSequence](loadfromxml-method-in-class-sms_tasksequence) | Loads a task sequence into WMI objects from XML. |
| [SaveToXml Method in Class SMS_TaskSequence](savetoxml-method-in-class-sms_tasksequence) | Serializes a task sequence from WMI objects to XML. |

## Properties

`SchemaVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

The version of the task sequence schema. The default version number is 3.00.

Although this property is designated as read/write in WMI, your application should not change it. The schema version must match the version that is detected by the client, or the client does not run the task sequence.

`Steps` Data type: `SMS_TaskSequence_Step` Array

Access type: Read/Write

Qualifiers: None

[SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class) objects representing steps and conditions in the task sequence.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Provider("TaskSequenceProvider")

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    A task sequence is a series of steps and conditions that are processed during operating system deployment.

    A step in the task sequence is usually an action, represented by the [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class) or a derived class. A task sequence step can also be a set of actions in a group, represented by [SMS_TaskSequence_Group Server WMI Class](sms_tasksequence_group-server-wmi-class). For more information, see [SMS_TaskSequence_Step Server WMI Class](sms_tasksequence_step-server-wmi-class).

    Task sequence steps are managed using WMI. The sequence steps are processed in order and can have conditions associated with them that determine how the action, or group of actions, is processed. For more information, see Operating System Deployment Task Sequence Object Model.

    Your application uses `SMS_TaskSequence` objects through a [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class) object, which supports a `Sequence` property to wrap the task sequence in the database. The application sets up a new task sequence by calling the [SetSequence Method in Class SMS_TaskSequencePackage](setsequence-method-in-class-sms_tasksequencepackage) and accesses an existing task sequence using the [GetSequence Method in Class SMS_TaskSequencePackage](getsequence-method-in-class-sms_tasksequencepackage). For more information about working with a task sequence, see How to Create an Operating System Deployment Task Sequence and How to Create an Operating System Deployment Task Sequence Package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).