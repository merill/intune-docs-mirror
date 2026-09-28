---
layout: Conceptual
title: RetryContentReplication Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/retrycontentreplication-method-in-class-sms_cm_updatepackages
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
description: The RetryContentReplication Windows Management Instrumentation (WMI) class method triggers DistMgr to copy content from the source to the content library.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2b4ded85-0700-d15a-a454-f8deb5604f77
document_version_independent_id: c479d56c-ec6a-2b71-204c-469716fc3c14
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/retrycontentreplication-method-in-class-sms_cm_updatepackages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/retrycontentreplication-method-in-class-sms_cm_updatepackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/retrycontentreplication-method-in-class-sms_cm_updatepackages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 19191404-a3bf-7d9a-afb5-1c8a2982111b
---

# RetryContentReplication Method - Configuration Manager | Microsoft Learn

The `RetryContentReplication` Windows Management Instrumentation (WMI) class method, in Configuration Manager, triggers DistMgr to copy content from the source to the content library.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RetryContentReplication(
     UInt32 ForceRetry
);

```

#### Parameters

`ForceRetry` Data type: `UInt32`

Qualifiers: [in, optional]

Flag to force a retry. 1 to force a retry; otherwise 0 or `null`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).