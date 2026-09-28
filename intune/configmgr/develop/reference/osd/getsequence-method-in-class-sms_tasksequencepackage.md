---
layout: Conceptual
title: GetSequence Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage
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
description: The GetSequence Windows Management Instrumentation (WMI) class method gets a task sequence (SMS_TaskSequence Server WMI Class) from a task sequence package (SMS_TaskSequencePackage Server WMI Class.)
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b3de7cbd-7834-f99a-9892-0612a96718fd
document_version_independent_id: c87c0205-a503-0d65-e26a-a019874b1b30
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1030ae16-3ee8-c59c-dcda-dd8fe8cb162b
---

# GetSequence Method - Configuration Manager | Microsoft Learn

The `GetSequence` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets a task sequence ([SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class)) from a task sequence package ([SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class)).

The following syntax is simplified from Managed Object Format (MOF) code, and it defines the method.

## Syntax

```
SInt32 GetSequence(
      SMS_TaskSequencePackage TaskSequencePackage,
      SMS_TaskSequence TaskSequence
);
```

#### Parameters

`TaskSequencePackage` Data type: `SMS_TaskSequencePackage`

Qualifiers: [in]

The task sequence package that contains the requested task sequence. See [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class).

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: [out]

The [SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class) object that represents the task sequence contained in the task sequence package specified in `TaskSequencePackage`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

Note

The task sequence is returned in the `TaskSequence` parameter.

## Remarks

You use `GetSequence` to get a [SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class) WMI object that represents a task sequence from a task sequence package. With this object, you can make changes to the task sequence and then update the task sequence package by using the [SetSequence Method in Class SMS_TaskSequencePackage](setsequence-method-in-class-sms_tasksequencepackage).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).