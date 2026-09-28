---
layout: Conceptual
title: AddLicense Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/addlicense-method-in-class-sms_deploymenttypelicenseassociation
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
description: The AddLicense Windows Management Instrumentation (WMI) class method adds license information to an application deployment type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2eb60818-5d1e-b621-c7bb-21b6c9150520
document_version_independent_id: 98ac0cb5-7f66-4c3d-3bdf-e5731f9865a3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/addlicense-method-in-class-sms_deploymenttypelicenseassociation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/addlicense-method-in-class-sms_deploymenttypelicenseassociation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/addlicense-method-in-class-sms_deploymenttypelicenseassociation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 548ee766-1e87-9272-44d5-6636d4fa3b2e
---

# AddLicense Method - Configuration Manager | Microsoft Learn

The `AddLicense` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds license information to an application deployment type.

## Syntax

```
sint32 AddLicense (
     [in] string LicenseID,
     [in] string LicenseBlob,
     [in] string ModelName
);

```

#### Parameters

`LicenseID` Data type: `String`

Qualifiers: [in]

The ID of the license.

`LicenseBlob` Data type: `String`

Qualifiers: [in]

The license blob.

`ModelName` Data type: `String`

Qualifiers: [in]

The model name of the deployment type.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).