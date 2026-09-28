---
layout: Conceptual
title: FindResourceSite method in class SMS_Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/findresourcesite-method-in-class-sms_collection
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
description: In Configuration Manager, the FindResourceSite WMI class method gets site code information for resources.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fb6b9316-d5fb-e124-550d-54a8627895fa
document_version_independent_id: e4002072-35a7-f031-d61b-4058fb8a08ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/findresourcesite-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/findresourcesite-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/findresourcesite-method-in-class-sms_collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6e73b802-8a8a-df08-a130-8c14297a720d
---

# FindResourceSite method in class SMS_Collection - Configuration Manager | Microsoft Learn

The `FindResourceSite` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets site code information for resources.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 FindResourceSite(
        boolean IncludeSubCollections = false,
        string SiteCode[],
        uint32 ResourceNumber[]
);

```

#### Parameters

`IncludeSubCollections` Data type: `Boolean`

Qualifiers: [in, optional, deprecated]

true if subcollections are also marked for evaluation. If this parameter is set to false, subcollections are not included. The value defaults to false, if not specified.

`SiteCode[]` Data type: `String` Array

Qualifiers: [out]

Site code of the site with which the resource is associated.

`ResourceNumber` Data type: `UInt32` Array

Qualifiers: [out]

Configuration Manager supplied ID that uniquely identifies a client resource.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).