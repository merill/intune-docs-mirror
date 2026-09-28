---
layout: Conceptual
title: RemoveContent method in class SMS_ContentPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removecontent-method-in-class-sms_contentpackage
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
description: Learn how to use the RemoteContent class method to remove the content for the given content ID from a package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3843b6e6-d6a2-5c4b-ece8-876ae8115471
document_version_independent_id: dc8c1304-6eaa-098a-0839-78c144d0ace2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/removecontent-method-in-class-sms_contentpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/removecontent-method-in-class-sms_contentpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/removecontent-method-in-class-sms_contentpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5955827a-8e1e-2b9a-0eb9-597a700b2353
---

# RemoveContent method in class SMS_ContentPackage - Configuration Manager | Microsoft Learn

The `RemoveContent` Windows Management Instrumentation (WMI) class method, in Configuration Manager, removes the content for the given content ID from the package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 RemoveContent(
     uint32  ContentIDs[],
     boolean bRefreshDPs[],
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: `[in, optional]`

Content identifiers for content to be removed.

`bRefreshDPs` Data type: `Boolean` Array

Qualifiers: `[in]`

`true`, if distribution points should be refreshed. The default value is `true`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).