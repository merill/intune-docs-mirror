---
layout: Conceptual
title: CCM_DTS_FLAG Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_dts_flag-enumeration
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
description: The CCM_DTS_FLAG enumeration indicates special options on download jobs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e7ec8cc8-648f-485c-564d-fcabf4abd3df
document_version_independent_id: 984888a4-58f1-b608-e7a7-93864f9bbbfb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ccm_dts_flag-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ccm_dts_flag-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ccm_dts_flag-enumeration.md
cmProducts: []
platformId: ca4805bd-8884-ce94-b486-34d52984e311
---

# CCM_DTS_FLAG Enumeration - Configuration Manager | Microsoft Learn

The **CCM\_DTS\_FLAG** enumeration indicates special options on download jobs.

## Syntax

```
typedef enum
{
    CCM_DTS_FLAG_SINGLEFILE             = 0x00000001,
    CCM_DTS_FLAG_DIRECTORY              = 0x00000002,
    CCM_DTS_FLAG_NOTIFYPROGRESS         = 0x00000004,
    CCM_DTS_FLAG_INSECURETRANSPORT      = 0x00000008,
    CCM_DTS_FLAG_TOPLEVELFILESONLY      = 0x00000010,
    CCM_DTS_FLAG_SENDAUTHHEADERS        = 0x00000020,
    CCM_DTS_FLAG_SENDAUTHHEADERS_MIXED  = 0x00000040,
    CCM_DTS_FLAG_USEINPUTMANIFEST       = 0x00000080,
    CCM_DTS_FLAG_SKIPHOSTCHANGEHANDLING = 0x00000100
}
CCM_DTS_FLAG;

```

## Members

| CTS flag | Description |
| --- | --- |
| CCM\_DTS\_FLAG\_SINGLEFILE | Reserved. |
| CCM\_DTS\_FLAG\_DIRECTORY | Indicates that `szRemotePath` is a directory and that all of its contents should be downloaded. This should always be specified in the case of alternate providers. |
| CCM\_DTS\_FLAG\_NOTIFYPROGRESS | This indicates that progress notifications are required. Even if this flag is not specified, success and error notifications are still required. |
| CCM\_DTS\_FLAG\_INSECURETRANSPORT | Reserved. |
| CCM\_DTS\_FLAG\_TOPLEVELFILESONLY | Reserved. |
| CCM\_DTS\_FLAG\_SENDAUTHHEADERS | Reserved. |
| CCM\_DTS\_FLAG\_SENDAUTHHEADERS\_MIXED | Reserved. |
| CCM\_DTS\_FLAG\_USEINPUTMANIFEST | Reserved. |
| CCM\_DTS\_FLAG\_SKIPHOSTCHANGEHANDLING | Reserved. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).