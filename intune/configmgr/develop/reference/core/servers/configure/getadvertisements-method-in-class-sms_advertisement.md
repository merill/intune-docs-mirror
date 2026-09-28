---
layout: Conceptual
title: GetAdvertisements Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getadvertisements-method-in-class-sms_advertisement
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
description: A Windows Management Instrumentation class method that gets the advertisement ID for a computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 60f7f301-2b5b-f060-69c0-8590f8db913a
document_version_independent_id: 5ac9dd76-5c72-5584-5a0c-bed326e5a107
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getadvertisements-method-in-class-sms_advertisement.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getadvertisements-method-in-class-sms_advertisement
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getadvertisements-method-in-class-sms_advertisement.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7ffcd7ba-0d7c-168e-98ea-481452e77217
---

# GetAdvertisements Method - Configuration Manager | Microsoft Learn

The `GetAdvertisements` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the advertisement id for a computer.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 GetAdvertisements(
     uint32  ResourceID,
     string  AdvertisementIDs[]
);
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: `[in]`

Unique Configuration Manager-supplied ID for the resource.

`AdvertisementIDs` Data type: `String` Array

Qualifiers: `[out]`

An array of unique auto-generated keys that Configuration Manager assigns to advertisements.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).