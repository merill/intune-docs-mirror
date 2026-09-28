---
layout: Conceptual
title: AddContent Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addcontent-method-in-class-sms_contentpackage
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
description: Learn how to add content to the SMS_ContentPackage Server WMI Class content package using AddContent.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 85be8c09-bfe4-ece5-994d-d5bb1acb7381
document_version_independent_id: 57a78b10-8925-abee-5051-5e3f5c718546
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/addcontent-method-in-class-sms_contentpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/addcontent-method-in-class-sms_contentpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/addcontent-method-in-class-sms_contentpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 80455ff6-d5ab-b4f5-9737-56731bfd89e3
---

# AddContent Method - Configuration Manager | Microsoft Learn

The `AddContent` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds content to the [SMS_ContentPackage Server WMI Class](sms_contentpackage-server-wmi-class) content package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 AddContent (
     string ContentID[],
     uint32 ContentVersion[]
     string ContentSource[],
     uint32 ContentFlags[]
     uint32 ContentType[],
     string RelatedContentID[]
);
```

#### Parameters

`ContentID` Data type: `string` Array

Qualifiers: `[in]`

Identifier of the content.

`ContentVersion` Data type: `UInt32` Array

Qualifiers: `[in]`

Version of the content.

`ContentSource` Data type: `String` Array

Qualifiers: `[in]`

Specifies the source location where content files are stored.

`ContentFlags` Data type: `UInt32` Array

Qualifiers: `[in]`

This specifies additional attributes for the content instance.

| Value | Content flag |
| --- | --- |
| 8 | DOWNLOAD\_ON\_DEMAND\_FROM\_LOCAL\_DP |
| 12 | DOWNLOAD\_FROM\_LOCAL\_DISPPOINT |
| 13 | DOWNLOAD\_LOCAL\_PARTIALDOWNLOADTOLOCAL |
| 14 | DOWNLOAD\_FROM\_REMOTE\_DISPPOINT |
| 15 | DOWNLOAD\_REMOTE\_PARTIALDOWNLOADTOLOCAL |
| 16 | DOWNLOAD\_ENABLE\_PEER\_CACHING |
| 17 | DP\_NO\_FALLBACK\_UNPROTECTED |
| 24 | DO\_NOT\_DOWNLOAD |
| 25 | PERSIST\_IN\_CACHE |

`ContentType` Data type: `UInt32` Array

Qualifiers: `[in]`

Specifies the type of content.

`RelatedContentID` Data type: `string` Array

Qualifiers: `[in]`

Specifies the related content associated with this content.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

The input parameters are a parallel array for each content element.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).