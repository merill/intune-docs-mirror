---
layout: Conceptual
title: GetTotalNumResults Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/gettotalnumresults-method-in-class-sms_collection
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
description: The GetTotalNumResults Windows Management Instrumentation class method gets a count of all members in a collection, including subcollections.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ae009380-0368-5628-6ef9-8a77c19a3cc9
document_version_independent_id: 1a14eca9-9e90-1a70-d491-636a98519f41
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/gettotalnumresults-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/gettotalnumresults-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/gettotalnumresults-method-in-class-sms_collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6fe1fb3b-f877-e16c-2604-1175a1ceca64
---

# GetTotalNumResults Method - Configuration Manager | Microsoft Learn

The `GetTotalNumResults` Windows Management Instrumentation (WMI) class method gets a count of all members in a collection, including subcollections.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetTotalNumResults(
     ref:SMS_Collection Collection,
     UInt32 Result
);
```

#### Parameters

`Collection` Data type: `ref:SMS_Collection`

Qualifiers: [in]

Collection ID or object path of the collection. The collection ID is the value of the `CollectionID` property of [SMS_Collection Server WMI Class](sms_collection-server-wmi-class).

`Result` Data type: `UInt32`

Qualifiers: [out]

Number of collection members, including subcollections.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).