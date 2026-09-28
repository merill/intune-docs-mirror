---
layout: Conceptual
title: CheckPortalUrl Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/checkportalurl-method-for-class-sms_clientsettings
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
description: Learn how to check if the default application catalog website point in the client agent settings is set to portalUrl.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 815af0e6-9d3a-7520-a5cb-2621b3d1ca3a
document_version_independent_id: 4a09d004-f72f-c62c-48fb-e854e83a1482
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/checkportalurl-method-for-class-sms_clientsettings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/checkportalurl-method-for-class-sms_clientsettings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/checkportalurl-method-for-class-sms_clientsettings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c87fd30-d3f5-6c04-baa8-6494d47fd822
---

# CheckPortalUrl Method - Configuration Manager | Microsoft Learn

The `CheckPortalUrl` Windows Management Instrumentation (WMI) class method, in Configuration Manager, checks whether the default application catalog website point in the default or custom client agent settings is set to `portalUrl`.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 CheckPortalUrl(
     string PortalUrl,
     boolean isUsed
);
```

#### Parameters

`PortalUrl` Data type: `String`

Qualifiers: `[in]`

PortalUrl.

`isUsed` Data type: `Boolean`

Qualifiers: `[out]`

isUsed.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).