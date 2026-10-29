---
layout: Conceptual
title: ReloadImageProperties method in class SMS_OperatingSystemInstallPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage
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
description: Learn how to use the ReloadImageProperties method in class SMS_OperatingSystemInstallPackage reload metadata from the source .wim file and synchronize the metadata with the database.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 24ae8033-4cd9-40ef-9e5c-b9ef2222ba65
document_version_independent_id: 2dfb0628-ac48-2e74-25d4-622fadb70df4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 92ee6a48-be4a-ca9f-fc8b-991add7fdd36
---

# ReloadImageProperties method in class SMS_OperatingSystemInstallPackage - Configuration Manager | Microsoft Learn

The `ReloadImageProperties` Windows Management Instrumentation WMI class method, in Configuration Manager, reloads metadata from the source .wim file and synchronizes the metadata with the database.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ReloadImageProperties();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

Your application uses this method to update the .wim file associated with the operating system install package. The update is based on the location defined in the `PkgSourcePath` property of [SMS_OperatingSystemInstallPackage Server WMI Class](sms_operatingsysteminstallpackage-server-wmi-class).

The application must:

1. Establish a connection to the SMS Provider. For more information, see About the SMS Provider in Configuration Manager.
2. Get the `SMS_OperatingSystemInstallPackage` object to update.
3. Call the `ReloadImageProperties` method.
4. Commit the `SMS_OperatingSystemInstallPackage` object.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).