---
layout: Conceptual
title: ReloadImageProperties method in class SMS_BootImagePackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_bootimagepackage
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
description: Reloads image metadata from a boot image source .wim file and synchronizes the metadata with the database.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d63ca10d-5f50-7b5b-5daf-a8d5aa0f8549
document_version_independent_id: 41528316-5766-acfb-20a4-d465f87f9197
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_bootimagepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_bootimagepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_bootimagepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 263895e1-e355-a1e4-c09d-d961e13c5a0f
---

# ReloadImageProperties method in class SMS_BootImagePackage - Configuration Manager | Microsoft Learn

The `ReloadImageProperties` Windows Management Instrumentation WMI class method, in Configuration Manager, reloads image metadata from a boot image source .wim file and synchronizes the metadata with the database.

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

The application uses this method if the administrator changes the boot image source .wim file outside of the Configuration Manager console. The application should:

1. Establish a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../core/understand/sms-provider-fundamentals).
2. Obtain the [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class) object to update.
3. Call `ReloadImageProperties`.
4. Commit the `SMS_BootImagePackage` object.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).