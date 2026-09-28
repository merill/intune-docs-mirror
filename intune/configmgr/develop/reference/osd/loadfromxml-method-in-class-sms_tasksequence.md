---
layout: Conceptual
title: LoadFromXml Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/loadfromxml-method-in-class-sms_tasksequence
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
description: In Configuration Manager, the LoadFromXml WMI class method loads a task sequence into WMI objects from task sequence XML.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0e50bb41-cf4a-431f-2559-c22dc56add91
document_version_independent_id: 0354311f-0c36-9240-3c5f-789d6e41a0cd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/loadfromxml-method-in-class-sms_tasksequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/loadfromxml-method-in-class-sms_tasksequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/loadfromxml-method-in-class-sms_tasksequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 264b10bc-46be-90ec-2385-0fc1254a1f82
---

# LoadFromXml Method - Configuration Manager | Microsoft Learn

The `LoadFromXml` Windows Management Instrumentation (WMI) class method, in Configuration Manager, loads a task sequence into WMI objects from task sequence XML.

Caution

As of Configuration Manager SP1, `LoadFromXml` has been replaced by the `ImportSequence` method on the `SMS_TaskSequencePackage` server WMI class.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SMS_TaskSequence LoadFromXml(
      String Xml
);
```

#### Parameters

`Xml` Data type: `String`

Qualifiers: [in]

The task sequence XML to use to build the WMI objects.

## Return Values

An [SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class) object.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

Your application uses this method to import XML from an outside provider, for example, the user interface. It builds and returns a WMI object model based on the represented task sequence.

Caution

You should not make changes to task sequences by using the XML. Rather, you should use the task sequence object model to create and edit task sequences. For more information, see [Operating System Deployment Task Sequence Object Model](../../osd/operating-system-deployment-task-sequence-object-model).

Note

Use the [SetSequence Method in Class SMS_TaskSequencePackage](setsequence-method-in-class-sms_tasksequencepackage) method to add a task sequence to a task sequence package.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).