---
layout: Conceptual
title: ReloadImageProperties Method in SMS_ImagePackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage
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
description: In Configuration Manager, the ReloadImageProperties WMI class method reloads image metadata from an image source .wim file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6446a0fb-0d8d-f6f5-ff51-466272807659
document_version_independent_id: aa2c76c0-bff7-29dc-b85b-c45f8da137f2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 48c47894-8b6a-465a-297e-2d18a75b3073
---

# ReloadImageProperties Method in SMS_ImagePackage - Configuration Manager | Microsoft Learn

The `ReloadImageProperties` Windows Management Instrumentation (WMI) class method, in Configuration Manager, reloads image metadata from an image source .wim file and synchronizes the metadata with the database.

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

For an example of the use of this method, see [How to Update an Operating System Image Package in Configuration Manager](../../osd/how-to-update-an-operating-system-image-package).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).