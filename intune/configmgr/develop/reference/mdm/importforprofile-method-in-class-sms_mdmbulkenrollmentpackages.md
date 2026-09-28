---
layout: Conceptual
title: ImportForProfile Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/importforprofile-method-in-class-sms_mdmbulkenrollmentpackages
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
description: The ImportForProfile Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports an On-Premises Mobile Device Management (MDM) bulk enrollment package for a profile.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5c336964-e524-fb05-3854-ccf3fdf238e1
document_version_independent_id: 3c67a2cc-2b08-6032-446e-e12941481a98
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/importforprofile-method-in-class-sms_mdmbulkenrollmentpackages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/importforprofile-method-in-class-sms_mdmbulkenrollmentpackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/importforprofile-method-in-class-sms_mdmbulkenrollmentpackages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36f187cf-f73f-e91e-f004-376d40816e8b
---

# ImportForProfile Method - Configuration Manager | Microsoft Learn

The `ImportForProfile` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports an On-Premises Mobile Device Management (MDM) bulk enrollment package for a profile.

## Syntax

```
sint32 ImportForProfile(
     String ProfileGUID,
     String CertificateGUID,
     String PackageName,
     String Certificate
);

```

#### Parameters

`ProfileGUID` Data type: `String`

Qualifiers: [in]

The GUID of the profile.

`CertificateGUID` Data type: `String`

Qualifiers: [in]

The GUID of the certificate.

`PackageName` Data type: `String`

Qualifiers: [in]

Package name.

`Certificate` Data type: `String`

Qualifiers: [in]

The root certificate.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).