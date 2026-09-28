---
layout: Conceptual
title: GetPackageHash Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getpackagehash-method-in-class-sms_tasksequencepackage
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
description: Learn how to get the hash of a Configuration Manager package using GetPackageHash class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d00ca71b-820d-6917-199a-c5fb449711d9
document_version_independent_id: 1ddaf0f6-1170-b9e6-b753-26f850980c27
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/getpackagehash-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/getpackagehash-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/getpackagehash-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8249045e-c67e-18c2-5f49-46eaf949287d
---

# GetPackageHash Method - Configuration Manager | Microsoft Learn

The `GetPackageHash` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the hash of a Configuration Manager package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetPackageHash(
      String PackageID,
      UInt32 SourceVersion,
      String Hash,
      UInt32 HashVersion
);
```

#### Parameters

`PackageID` Data type: `String`

Qualifiers: [in]

ID of the task sequence package.

`SourceVersion` Data type: `UInt32`

Qualifiers: [in]

The version of the package available at the site. This version is indicated by the `SourceVersion` property of [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class).

`Hash` Data type: `String`

Qualifiers: [out]

The hash for the package content.

`HashVersion` Data type: `UInt32`

Qualifiers: [out]

The type of the requested hash which can be one of the following values.

1 - MD5 hash

2 - SHA-1 hash

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).