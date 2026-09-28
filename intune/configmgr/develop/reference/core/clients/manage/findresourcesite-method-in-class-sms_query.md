---
layout: Conceptual
title: FindResourceSite method in class SMS_Query - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/findresourcesite-method-in-class-sms_query
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
description: Article describing how to use FindResourceSite in Configuration Manager to get site code information for resources from SQL.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 35a769d4-0ee3-7f4e-e54a-f58e205ea8fb
document_version_independent_id: 1c97ad1b-9675-8415-8460-d9306a50d75e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/findresourcesite-method-in-class-sms_query.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/findresourcesite-method-in-class-sms_query
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/findresourcesite-method-in-class-sms_query.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dca8d305-a1f9-9d89-7240-d5a3f8acfffb
---

# FindResourceSite method in class SMS_Query - Configuration Manager | Microsoft Learn

The `FindResourceSite` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets site code information for resources from SQL.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 FindResourceSite(
   Boolean IncludeSubCollections,
   String SiteCode[],
   UInt32 ResourceNumber[]
);
```

#### Parameters

`IncludeSubCollections` Data type: `Boolean`

Qualifiers: [in, optional]

`true` if subcollections should be included. The default value is `false`.

`SiteCode` Data type: `String` Array

Qualifiers: [out]

Site code of the Configuration Manager site.

`ResourceNumber` Data type: `UInt32` Array

Qualifiers: [out]

The resource number.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).