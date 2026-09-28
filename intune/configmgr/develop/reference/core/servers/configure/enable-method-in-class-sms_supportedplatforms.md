---
layout: Conceptual
title: Enable Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/enable-method-in-class-sms_supportedplatforms
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
description: The Enable Windows Management Instrumentation (WMI) class method, in Configuration Manager, enables or disables the platforms.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 71b1f651-40c3-21b7-eac7-fc9a4af96ee1
document_version_independent_id: 5b761c65-2401-f071-2344-0c61777bb2b6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/enable-method-in-class-sms_supportedplatforms.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/enable-method-in-class-sms_supportedplatforms
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/enable-method-in-class-sms_supportedplatforms.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4be90220-a3ab-d010-20d0-d56f278bd560
---

# Enable Method - Configuration Manager | Microsoft Learn

The `Enable` Windows Management Instrumentation (WMI) class method, in Configuration Manager, enables or disables the platforms.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 Enable(
     boolean IsSupported
);
```

#### Parameters

`IsSupported` Data type: `Boolean`

Qualifiers: `[in]`

`true` if the platforms are enabled. The default value is `true`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).