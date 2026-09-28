---
layout: Conceptual
title: UploadToken Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/uploadtoken-method-in-class-sms_mdmapplevpptoken
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
description: The UploadToken WMI class method uploads an Apple Volume Purchase Program (VPP) token to Microsoft Intune.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e3d9eac7-0492-a122-3164-ced9b0d6c541
document_version_independent_id: e6511dc4-4241-33d1-a3be-f5cd028109b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/uploadtoken-method-in-class-sms_mdmapplevpptoken.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/uploadtoken-method-in-class-sms_mdmapplevpptoken
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/uploadtoken-method-in-class-sms_mdmapplevpptoken.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 084f6844-1b01-554b-09f6-4098ba07bcde
---

# UploadToken Method - Configuration Manager | Microsoft Learn

The `UploadToken` Windows Management Instrumentation (WMI) class method, in Configuration Manager, uploads an Apple Volume Purchase Program (VPP) token to Microsoft Intune.

## Syntax

```
sint32 UploadToken(
     String TokenID,
     String VppToken,
     String OrganizationName,
     String ExpirationDate
);

```

#### Parameters

`TokenID` Data type: `String`

Qualifiers: [in]

The ID of the Apple VPP token.

`VppToken` Data type: `String`

Qualifiers: [in]

Name of the token.

`OrganizationName` Data type: `String`

Qualifiers: [in]

Organization name for the token.

`ExpirationDate` Data type: `String`

Qualifiers: [in]

Expiration date of the token.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).