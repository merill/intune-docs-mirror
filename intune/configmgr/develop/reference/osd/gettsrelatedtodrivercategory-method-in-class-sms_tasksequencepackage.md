---
layout: Conceptual
title: GetTSRelatedToDriverCategory Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/gettsrelatedtodrivercategory-method-in-class-sms_tasksequencepackage
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
description: The GetTSRelatedToDriverCategory WMI class method gets task sequence packages related to the specified category.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f5a6786c-f5cf-cc60-27fd-e6a4a29bf206
document_version_independent_id: b35dfee3-c59f-0e16-ff96-fceed5d6b9f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/gettsrelatedtodrivercategory-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/gettsrelatedtodrivercategory-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/gettsrelatedtodrivercategory-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ac8f4858-ee9f-e941-f326-8898d736b05f
---

# GetTSRelatedToDriverCategory Method - Configuration Manager | Microsoft Learn

The `GetTSRelatedToDriverCategory` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that gets task sequence packages related to the specified category.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetTSRelatedToDriverCategory
{
    [IN]    String CategoryUniqueId,
    [OUT]   String PacakgeIds[]
    [OUT]   String PackageNames[]
};
```

## Parameters

`CategoryUniqueId` Data type: `String`

Qualifiers: [id("0"), in]

Unique ID of the category instance. This ID is unique across sites. The string length can be up to 512 characters.

`PacakgeIds` Data type: `String` Array

Qualifiers: [id("2"), out]

Package identifiers for packages related to the specified category.

Note

The incorrect spelling of the variable "PacakgeIds" is hardcoded in WMI.

`PackageNames` Data type: `String` Array

Qualifiers: [id("3"), out]

Package names for packages related to the specified category.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).