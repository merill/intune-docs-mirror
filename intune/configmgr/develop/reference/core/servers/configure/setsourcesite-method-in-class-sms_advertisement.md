---
layout: Conceptual
title: SetSourceSite method in class SMS_Advertisement - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/setsourcesite-method-in-class-sms_advertisement
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
description: Learn how the SetSourceSite Windows Management Instrumentation (WMI) class method, in Configuration Manager, sets the source site code for the advertisement.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2ced037f-b5f4-2737-b280-d894fe732c7f
document_version_independent_id: 807dc153-cc5a-aeee-ae40-0e7ec09f7b80
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/setsourcesite-method-in-class-sms_advertisement.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/setsourcesite-method-in-class-sms_advertisement
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/setsourcesite-method-in-class-sms_advertisement.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 47d84984-3122-db93-3421-e3c9efcc5580
---

# SetSourceSite method in class SMS_Advertisement - Configuration Manager | Microsoft Learn

The `SetSourceSite` Windows Management Instrumentation (WMI) class method, in Configuration Manager, sets the source site code for the advertisement.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 SetSourceSite(
     string SourceSite,
);
```

#### Parameters

`SourceSite` Data type: `String`

Qualifiers: `[in]`

The site code of the source site for the advertisement.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).