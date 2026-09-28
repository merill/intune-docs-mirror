---
layout: Conceptual
title: VerifyPackage Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/verifypackage-method-in-class-sms_distributionpoint
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
description: A class method that verifies the integrity of the files in a package by calculating the hash of each file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9228f6cf-01e0-2643-5325-bd1e44e0090e
document_version_independent_id: d2b55fc1-6f77-ec26-58d7-201a93c5692b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/verifypackage-method-in-class-sms_distributionpoint.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/verifypackage-method-in-class-sms_distributionpoint
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/verifypackage-method-in-class-sms_distributionpoint.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 740f7292-b41a-292b-3b1b-8e7c6d12ef1a
---

# VerifyPackage Method - Configuration Manager | Microsoft Learn

The `VerifyPackage` Windows Management Instrumentation (WMI) class method, in Configuration Manager, verifies the integrity of all the files in the package by calculating the hash of each file.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 VerifyPackage(
     string PackageId,
     string NALPath
);
```

#### Parameters

`PackageId` Data type: `String`

Qualifiers: `[in]`

ID for an existing package.

`NALPath` Data type: `String`

Qualifiers: `[in]`

Network abstraction layer (NAL) path to the distribution point server.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).