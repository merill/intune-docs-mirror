---
layout: Conceptual
title: RemoveSiteSystem method in class SMS_DefaultBoundaryGroup - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removesitesystem-method-in-class-sms-defaultboundarygroup
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
description: Learn how to remove one or more site system servers from a default boundary group using the RemoveSiteSystem class.
ms.date: 2017-03-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 87943dc5-abff-8652-4775-29e4129884ef
document_version_independent_id: 0eb9fca9-a0f3-da73-d92c-3e6979db1cbb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/removesitesystem-method-in-class-sms-defaultboundarygroup.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/removesitesystem-method-in-class-sms-defaultboundarygroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/removesitesystem-method-in-class-sms-defaultboundarygroup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8ef96f43-d4c8-bc83-3cf2-bc0ca6fe8d36
---

# RemoveSiteSystem method in class SMS_DefaultBoundaryGroup - Configuration Manager | Microsoft Learn

The `RemoveSiteSystem` Windows Management Instrumentation (WMI) class method, in Configuration Manager, removes one or more site system servers from a default boundary group.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RemoveSiteSystem(
    String ServerNALPath[]
);
```

### Parameters

`ServerNALPath` Data type: `String`

Qualifiers: [in]

Array of network abstraction layer (NAL) paths to one or more site system servers within the boundary group.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).