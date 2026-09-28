---
layout: Conceptual
title: GetClientConfigPolicies Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getclientconfigpolicies-method-in-class-sms_tasksequencepackage
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
description: The GetClientConfigPolicies WMI class method gets all site-wide client configuration policies and their corresponding policy assignments.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 40b753c8-4ffd-722a-ff05-677b33daba86
document_version_independent_id: 932f25a8-dc1f-61f1-3937-6759815cae34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/getclientconfigpolicies-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/getclientconfigpolicies-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/getclientconfigpolicies-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 391848cd-c0da-20d2-6eaa-376752f66344
---

# GetClientConfigPolicies Method - Configuration Manager | Microsoft Learn

The `GetClientConfigPolicies` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets all site-wide client configuration policies and their corresponding policy assignments.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetClientConfigPolicies(
      String PolicyXmls[],
      String PolicyAssignmentXmls[]
);
```

#### Parameters

`PolicyXmls` Data type: `String` Array

Qualifiers: [out]

The XML representations of all site-wide client configuration policies.

`PolicyAssignmentXmls` Data type: `String` Array

Qualifiers: [out]

The XML representations of all site-wide client configuration policy assignments. This parameter and `PolicyXmls` are aligned, with the nth element of one corresponding to the nth element of the other.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).