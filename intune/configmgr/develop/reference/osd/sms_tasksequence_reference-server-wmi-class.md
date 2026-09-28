---
layout: Conceptual
title: SMS_TaskSequence_Reference Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class
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
description: The SMS_TaskSequence_Reference Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents the package ID and optional program name.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bb7ce3b8-2277-4a89-8390-296ae2d720b9
document_version_independent_id: 770893be-8bdb-71ef-e72e-625c81004142
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 28f7c933-eb40-4690-2b15-22b0267ef2f2
---

# SMS_TaskSequence_Reference Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_Reference` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the package ID and optional program name used by the task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_Reference
{
      String Package;
      String Program;
      UInt32 Type
};
```

## Methods

The `SMS_TaskSequence_Reference` class does not define any methods.

## Properties

`Package` Data type: `String`

Access type: Read/Write

Qualifiers: None

If `Type` is 0, the identifier of the package. If `Type` is 1, the identifier of the application (the model name).

`Program` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional. The name of the program associated with the package. See [SMS_Program Server WMI Class](../core/servers/configure/sms_program-server-wmi-class).

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The type of reference. The possible values are:

| Value | Reference type |
| --- | --- |
| 0 | Package Reference |
| 1 | Application Reference |

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Your application can obtain the packages referenced by a task sequence from the `References` property of [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).