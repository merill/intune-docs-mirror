---
layout: Conceptual
title: CheckDuplicateShareName Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/checkduplicatesharename-method-in-class-sms_package
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
description: Learn how to use CheckDuplicateShareName class to determine if the specified share name has been used by another package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6cdea3a8-281a-0663-9ee6-13f9a079a302
document_version_independent_id: c794d851-3bab-c128-a778-375706ec1a7a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/checkduplicatesharename-method-in-class-sms_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/checkduplicatesharename-method-in-class-sms_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/checkduplicatesharename-method-in-class-sms_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 29d6dc1e-d150-b84b-5661-ee6735801e7f
---

# CheckDuplicateShareName Method - Configuration Manager | Microsoft Learn

The `CheckDuplicateShareName` Windows Management Instrumentation (WMI) class method, in Configuration Manager, determines if the specified share name has been used by another package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CheckDuplicateShareName(
     String ShareName,
     String PackageID,
     Boolean IsDuplicated,
      String DupPkgName,
     String DupPkgID,
     SInt32 DupPkgType
);
```

#### Parameters

`ShareName` Data type: `String`

Qualifiers: [in]

Share name defined for the package.

`PackageID` Data type: `String`

Qualifiers: [in]

ID of the package to which to add the share specified by `ShareName`.

`IsDuplicated` Data type: `Boolean`

Qualifiers: [out]

`true` if the share specified by `ShareName` has been used by another package.

`DupPkgName` Data type: `String`

Qualifiers: [out]

Name of the package using the share specified by `ShareName`.

`DupPkgID` Data type: `String`

Qualifiers: [out]

ID of the other package using the share specified by `ShareName`.

`DupPkgType` Data type: `SInt32`

Qualifiers: [out]

Type of package for which the share specified by `ShareName` is duplicated. Possible values are defined for the `PackageType` property of [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class). The default value is 1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).