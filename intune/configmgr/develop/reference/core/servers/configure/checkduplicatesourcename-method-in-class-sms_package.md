---
layout: Conceptual
title: CheckDuplicateSourceName Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/checkduplicatesourcename-method-in-class-sms_package
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
description: The CheckDuplicateSourceName Windows Management Instrumentation (WMI) class method determines if the specified source name is used by another package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 49b0b28e-96f1-3173-9c2a-c200cae4f781
document_version_independent_id: ebcbd018-d7ad-181c-566c-fa30b2302d59
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/checkduplicatesourcename-method-in-class-sms_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/checkduplicatesourcename-method-in-class-sms_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/checkduplicatesourcename-method-in-class-sms_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 01ea5073-c7f2-948b-4c29-9f7a44f5de88
---

# CheckDuplicateSourceName Method - Configuration Manager | Microsoft Learn

The `CheckDuplicateSourceName` Windows Management Instrumentation (WMI) class method, in Configuration Manager, determines if the specified source name is used by another package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CheckDuplicateSourceName(
     String SourceName,
     String SourceSite,
     Boolean IsDuplicated,
     String DupPkgName,
     String DupPkgID,
     SInt32 DupPkgType
);
```

#### Parameters

`SourceName` Data type: `String`

Qualifiers: [in]

Source name defined for the package.

`SourceSite` Data type: `String`

Qualifiers: [in]

ID of the package to which to add the source specified by `SourceName`.

`IsDuplicated` Data type: `Boolean`

Qualifiers: [out]

`true` if the source specified by `SourceName` has been used by another package.

`DupPkgName` Data type: `String`

Qualifiers: [out]

Name of the package using the source specified by `SourceName`.

`DupPkgID` Data type: `String`

Qualifiers: [out]

ID of the other package using the source specified by `SourceName`.

`DupPkgType` Data type: `SInt32`

Qualifiers: [out]

Type of package for which the source specified by `SourceName` is duplicated. Possible values are defined for the `PackageType` property of [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class). The default value is 1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).