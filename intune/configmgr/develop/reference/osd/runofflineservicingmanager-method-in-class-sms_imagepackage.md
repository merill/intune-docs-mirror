---
layout: Conceptual
title: RunOfflineServicingManager Method in SMS_ImagePackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/runofflineservicingmanager-method-in-class-sms_imagepackage
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
description: The RunOfflineServicingManager WMI class method updates the site control file of the offline servicing manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fafff983-4e9c-3e80-c060-245a435ca2ff
document_version_independent_id: 1814296d-8cf1-c916-1267-615dad89c981
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/runofflineservicingmanager-method-in-class-sms_imagepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/runofflineservicingmanager-method-in-class-sms_imagepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/runofflineservicingmanager-method-in-class-sms_imagepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e5d3f379-4cc2-a839-6b11-da15efb3de28
---

# RunOfflineServicingManager Method in SMS_ImagePackage - Configuration Manager | Microsoft Learn

The `RunOfflineServicingManager` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that updates the site control file of the offline servicing manager to run the offline image servicing component as soon as possible on the specified operating system image at the specified site server.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 RunOfflineServicingManager
{
    [IN]    String SiteCode
    [IN]    String ServerName
    [IN]    String PackageID
    [IN]    UInt32 PackageType
};
```

## Parameters

`SiteCode` Data type: `String`

Qualifiers: [id("0"), in]

Site code of the site where offline servicing of the operating system image is requested.

`ServerName` Data type: `String`

Qualifiers: [id("1"), in]

Name of the site server where offline servicing of the operating system is requested (server1.domain1.net).

`PackageID` Data type: `String`

Qualifiers: [id("2"), in]

The package identifier of the operating system image to be patched with software updates through offline servicing.

`PackageType` Data type: `UInt32`

Qualifiers: [id("3"), in]

The package type of the operating system image or operating system upgrade package.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).