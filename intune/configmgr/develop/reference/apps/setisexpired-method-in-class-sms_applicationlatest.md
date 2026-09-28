---
layout: Conceptual
title: SetIsExpired method in class SMS_ApplicationLatest - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/setisexpired-method-in-class-sms_applicationlatest
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
description: In Configuration Manager, the SetIsExpired WMI class method sets the expired status of this application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5a8b7e3e-ccdf-8444-98a2-b2639183b6ac
document_version_independent_id: 9c656637-065d-dd31-5405-42991ecbc096
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/setisexpired-method-in-class-sms_applicationlatest.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/setisexpired-method-in-class-sms_applicationlatest
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/setisexpired-method-in-class-sms_applicationlatest.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6630a7e8-0701-ccbf-a504-9c3e2712caca
---

# SetIsExpired method in class SMS_ApplicationLatest - Configuration Manager | Microsoft Learn

The `SetIsExpired` Windows Management Instrumentation (WMI) class method, in Configuration Manager, sets the expired status of this application.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 SetIsExpired (
     boolean Expired
);
```

#### Parameters

`Expired` Data type: `Boolean`

Qualifiers: [in]

`true` to set the state to expired. The default value is `true`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).