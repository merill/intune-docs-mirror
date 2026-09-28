---
layout: Conceptual
title: SetSequence Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage
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
description: The SetSequence Windows Management Instrumentation (WMI) class method, in Configuration Manager, updates the task sequence package with the specified task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ed15a70b-31b0-70e8-ec36-b2796a786c64
document_version_independent_id: c309ecbb-aa43-4a40-d6fc-c914629811e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2243c872-1e4c-f5cb-0a2e-e321b92f67e2
---

# SetSequence Method - Configuration Manager | Microsoft Learn

The `SetSequence` Windows Management Instrumentation (WMI) class method, in Configuration Manager, updates the task sequence package with the specified task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 SetSequence(
      SMS_TaskSequencePackage TaskSequencePackage,
      SMS_TaskSequence TaskSequence,
      String SavedTaskSequencePackagePath
);
```

#### Parameters

`TaskSequencePackage` Data type: `SMS_TaskSequencePackage`

Qualifiers: [in]

The package that the task sequence `TaskSequence` is added to. See [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class).

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: [in]

The [SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class) object that represents the task sequence that is added to `TaskSequencePackage`.

`SavedTaskSequencePackagePath` Data type: `String`

Qualifiers: [out]

The relative WMI object path for the updated task sequence package.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

`SetSequence` is used to associate a task sequence ([SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class)) with a task sequence package.

This method also updates other properties of the task sequence package, for example, package references and task sequence type, based on the specified task sequence.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).