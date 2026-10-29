---
layout: Conceptual
title: AddUpdateContent Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage
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
description: In Configuration Manager, the AddUpdateContent WMI class method downloads content to a software update package and replicates the content to distribution points.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 084bcd4f-72bb-3121-00d4-b642effeffae
document_version_independent_id: ecbf720f-5432-e4a3-f96b-ae4ca35a71dd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5621a1ce-c8cc-a6b1-aa36-f9e02073635d
---

# AddUpdateContent Method - Configuration Manager | Microsoft Learn

The `AddUpdateContent` Windows Management Instrumentation (WMI) class method, in Configuration Manager, downloads content to a software update package and replicates the content to distribution points.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddUpdateContent(
     UInt32 ContentIDs[],
     String ContentSourcePath[],
     Boolean bRefreshDPs
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: [in]

IDs of contents to add to the software updates package.

`ContentSourcePath` Data type: `String` Array

Qualifiers: [in]

The source path where the content files are located.

`bRefreshDPs` Data type: `Boolean`

Qualifiers: [in, optional]

`true` (default) to replicate package content to the distribution points.

## Return Values

The method returns an exception on failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

This method first creates the [SMS_SoftwareUpdatesPackage Server WMI Class](sms_softwareupdatespackage-server-wmi-class) object and then adds the indicated content. Your application can use [SMS_CIToContent Server WMI Class](sms_citocontent-server-wmi-class) and [SMS_CIContentFiles Server WMI Class](sms_cicontentfiles-server-wmi-class) to determine the content.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).