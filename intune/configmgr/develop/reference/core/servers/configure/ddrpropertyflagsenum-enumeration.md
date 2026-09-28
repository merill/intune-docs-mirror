---
layout: Conceptual
title: DDRPropertyFlagsEnum Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration
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
description: Learn how to use the DDRPropertyFlagsEnum enumeration in Configuration Manager which specifies flags that are used by ISMSResGen.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ae61e4a7-b641-985d-faee-dfd96e6bd3ef
document_version_independent_id: 5ba301a9-da7c-9e0d-c0af-d75a42462bef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 855a8983-5775-86f5-ab9d-f399875992ba
---

# DDRPropertyFlagsEnum Enumeration - Configuration Manager | Microsoft Learn

The `DDRPropertyFlagsEnum` enumeration, in Configuration Manager, specifies flags that are used by `ISMSResGen`.

## Syntax

```
enum DDRPropertyFlagsEnum
{
    ADDPROP_NONE = 0x0,
    ADDPROP_GUID = 0x00000002,
    ADDPROP_GROUPING = 0x00000004,
    ADDPROP_KEY = 0x00000008,
    ADDPROP_ARRAY = 0x00000010,
    ADDPROP_AGENT = 0x00000020,
    ADDPROP_NAME = 0x00000044,
    ADDPROP_NAME2 = 0x00000084
};
```

## Elements

ADDPROP\_NONE(0x0) No special properties.

ADDPROP\_GUID(0x00000002) Defines this property as being a GUID.

ADDPROP\_GROUPING(0x00000004) Reserved.

ADDPROP\_KEY(0x00000008) Defines this property as being a Key value that must be unique.

ADDPROP\_ARRAY(0x00000010) Reserved.

ADDPROP\_AGENT(0x00000020) Reserved.

ADDPROP\_NAME(0x00000044) Specifies this property as the actual `Name` property in the resource.

ADDPROP\_NAME2(0x00000084) Specifies this property as the actual `Comment` property in the resource.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).