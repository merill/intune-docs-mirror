---
layout: Conceptual
title: Deny Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/deny-method-in-class-sms_userapplicationrequest
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
description: The Deny Windows Management Instrumentation (WMI) class method, in Configuration Manager, denies user application requests.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8e7cccf3-0f7b-d02e-3dc0-f758032069eb
document_version_independent_id: 0f014d89-53f2-3686-7ae9-203201eb4cb0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/deny-method-in-class-sms_userapplicationrequest.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/deny-method-in-class-sms_userapplicationrequest
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/deny-method-in-class-sms_userapplicationrequest.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4c8bbc2f-fca8-3115-4267-b4590d3103a7
---

# Deny Method - Configuration Manager | Microsoft Learn

The `Deny` Windows Management Instrumentation (WMI) class method, in Configuration Manager, denies user application requests.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 Deny(
     string Comments
);
```

#### Parameters

`Comments` Data type: `String` Array

Qualifiers: [in, SizeLimit("2000")]

Comments regarding the denial of the application request.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).