---
layout: Conceptual
title: CCM_DTS_PRIORITY enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_dts_priority-enumeration
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
description: The CCM_DTS_PRIORITY enumeration indicates the priority of the download.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 473ff6f5-8fe9-a8ee-807d-f49f25a04f04
document_version_independent_id: 64c9b28c-32ad-b9ca-534d-2e49eedaafb9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ccm_dts_priority-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ccm_dts_priority-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ccm_dts_priority-enumeration.md
cmProducts: []
platformId: 439a1577-5e17-fe07-1dd8-cd839a2d3c70
---

# CCM_DTS_PRIORITY enumeration - Configuration Manager | Microsoft Learn

The **CCM\_DTS\_PRIORITY** enumeration indicates the priority of the download.

## Syntax

```
typedef enum
{
    CCM_DTS_PRIORITY_FOREGROUND,
    CCM_DTS_PRIORITY_HIGH,
    CCM_DTS_PRIORITY_NORMAL,
    CCM_DTS_PRIORITY_LOW,
}CCM_DTS_PRIORITY;

```

## Members

| Priority flag | Description |
| --- | --- |
| CCM\_DTS\_PRIORITY\_FOREGROUND | The highest priority. |
| CCM\_DTS\_PRIORITY\_HIGH | High priority. |
| CCM\_DTS\_PRIORITY\_NORMAL | Normal priority. |
| CCM\_DTS\_PRIORITY\_LOW | Low priority. |

## Remarks

The only strict requirement is that jobs at a lower priority do not block progress of jobs at a higher priority. Providers must respect this.

## Requirements

### Runtime requirements

For more information, see [Configuration Manager client runtime requirements](../../../../core/reqs/client-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager client development requirements](../../../../core/reqs/client-development-requirements).