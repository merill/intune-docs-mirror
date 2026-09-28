---
layout: Conceptual
title: Refresh method in class SMS_ResourceMap - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/refresh-method-in-class-sms_resourcemap
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
description: The Refresh Windows Management Instrumentation class method, in Configuration Manager, updates resource and inventory class definitions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 36ad3a7d-ce9c-926a-a905-3dc5e1020d3a
document_version_independent_id: a9980b85-ab32-25b5-bf57-389906284872
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/refresh-method-in-class-sms_resourcemap.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/refresh-method-in-class-sms_resourcemap
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/refresh-method-in-class-sms_resourcemap.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7cb8dbb6-9531-0588-52de-8107e9f7dfdb
---

# Refresh method in class SMS_ResourceMap - Configuration Manager | Microsoft Learn

The `Refresh` Windows Management Instrumentation (WMI) class method, in Configuration Manager, updates resource (classes derived from [SMS_R_System Server WMI Class](sms_r_system-server-wmi-class)) and inventory (classes derived from [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class)) class definitions.

The following syntax is simplified from Manage Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 Refresh();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).