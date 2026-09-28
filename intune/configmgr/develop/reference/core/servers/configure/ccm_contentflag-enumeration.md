---
layout: Conceptual
title: CCM_CONTENTFLAG Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_contentflag-enumeration
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
description: Learn about the CCM_CONTENTFLAG Enumeration that contains options for transferring content.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3ae4d0d8-ad5a-0073-6358-8f9e036beea1
document_version_independent_id: d838daf8-d05d-746b-2776-7f34deeb37db
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ccm_contentflag-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ccm_contentflag-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ccm_contentflag-enumeration.md
cmProducts: []
platformId: ddcaad5e-76fb-2db1-8523-c79bc403f4a4
---

# CCM_CONTENTFLAG Enumeration - Configuration Manager | Microsoft Learn

The **CCM\_CONTENTFLAG** enumeration contains options for transferring content.

## Syntax

```vb
typedef enum
{
    CCM_CONTENTFLAG_LOCAL_ONLY                  = 0x00000001,
    CCM_CONTENTFLAG_REMOTE_ONLY                 = 0x00000002,
    CCM_CONTENTFLAG_LOCAL_OR_REMOTE             = 0x00000004,
    CCM_CONTENTFLAG_PROTECTED_ONLY              = 0x00000008,
    CCM_CONTENTFLAG_ALLOW_CACHING               = 0x00000010,
    CCM_CONTENTFLAG_PEERDP                      = 0x00000020,
    CCM_CONTENTFLAG_REMOTE_NOLOCALPEERDP        = 0x00000040,
    CCM_CONTENTFLAG_DELTA_DOWNLOAD              = 0x00000080,
    CCM_CONTENTFLAG_ALLOW_ALTERNATE_PROVIDERS   = 0x00000100
}
CCM_CONTENTFLAG;
```

## Members

| Content flag | Description |
| --- | --- |
| CCM\_CONTENTFLAG\_LOCAL\_ONLY | Local only. |
| CCM\_CONTENTFLAG\_REMOTE\_ONLY | Remote only. |
| CCM\_CONTENTFLAG\_LOCAL\_OR\_REMOTE | Local or remote. |
| CCM\_CONTENTFLAG\_PROTECTED\_ONLY | Protected only. |
| CCM\_CONTENTFLAG\_ALLOW\_CACHING | Allow caching. |
| CCM\_CONTENTFLAG\_PEERDP | Branch distribution point. |
| CCM\_CONTENTFLAG\_REMOTE\_NOLOCALPEERDP | No local branch distribution point. |
| CCM\_CONTENTFLAG\_DELTA\_DOWNLOAD | Delta download. |
| CCM\_CONTENTFLAG\_ALLOW\_ALTERNATE\_PROVIDERS | Allow alternate providers. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).