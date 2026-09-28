---
layout: Conceptual
title: ValidateNewPackageSource method in class SMS_DriverPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage
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
description: Learn how to validate a new location for a driver update using ValidateNewPackageSource class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cb888adb-07c7-3c98-484e-81b162c70893
document_version_independent_id: 922a5eb9-b060-f884-ba48-86e749c04fc5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c336382-7d1e-2423-0a0b-fdfd9d0b0c0d
---

# ValidateNewPackageSource method in class SMS_DriverPackage - Configuration Manager | Microsoft Learn

The `ValidateNewPackageSource` Windows Management Instrumentation (WMI) class method, in Configuration Manager, validates a new location for a driver update.

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

The driver package content to verify.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

This method is new in the latest version of Configuration Manager. Note that it is the only way to change the package source for an [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) object. Most other types of packages can be changed in the console, but not the driver package. The access to this package from the console is restricted.

To use this method:

1. Manually copy the package files from the old source location to the new location.
2. In your application, obtain an [SMS_DriverPackage Server WMI Class](sms_driverpackage-server-wmi-class) object for the driver.
3. Include a call to `ValidateNewPackageSource` on the package.
4. On successful return from the method, have the application change the `StoredPkgPath` property in the package to indicate the new source location.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).