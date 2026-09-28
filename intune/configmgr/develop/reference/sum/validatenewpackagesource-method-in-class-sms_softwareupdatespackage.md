---
layout: Conceptual
title: ValidateNewPackageSource method in class SMS_SoftwareUpdatesPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage
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
description: Learn how to use the ValidateNewPackageSource class method to validate a new package source location for a software update.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 36010f5e-ea2f-d7c3-f67f-2c7d92c38d9f
document_version_independent_id: 83cb25e9-1fc2-a0c0-075c-dc3ef8f6f24e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2f2b6560-2219-9e10-8ef2-fa7b0c6c182c
---

# ValidateNewPackageSource method in class SMS_SoftwareUpdatesPackage - Configuration Manager | Microsoft Learn

The `ValidateNewPackageSource` Windows Management Instrumentation (WMI) class method, in Configuration Manager, validates a new package source location for a software update.

Note

All of the updates available in the old package source must be available in the new package source for validation to succeed.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ValidateNewPackageSource(  
     String PackageSource  
);  
```

#### Parameters

`PackageSource` Data type: `String`

Qualifiers: [in]

The location of the package content to verify.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

This method might be used when changing the package source location of a software update package due to infrastructure changes or a server failure.

This method is new in the latest version of Configuration Manager. Note that it is the only way to change the package source for an [SMS_SoftwareUpdate Server WMI Class](sms_softwareupdate-server-wmi-class) object. Most other types of packages can be changed in the console, but not the software update package. The access to this package from the console is restricted.

To use this method:

1. Manually copy the package files from the old source location to the new location.
2. In your application, obtain the [SMS_SoftwareUpdatesPackage Server WMI Class](sms_softwareupdatespackage-server-wmi-class) object for the software update.
3. Include a call to `ValidateNewPackageSource` on the package.
4. On successful return from the method, have the application change the `StoredPkgPath` property in the package to indicate the new source location.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).