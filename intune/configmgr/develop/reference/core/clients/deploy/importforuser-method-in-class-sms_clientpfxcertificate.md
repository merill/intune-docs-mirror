---
layout: Conceptual
title: ImportForUser Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/importforuser-method-in-class-sms_clientpfxcertificate
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
description: The ImportForUser Windows Management Instrumentation class method, in Configuration Manager, imports a certificate for a user, encrypted by using a password.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dd41bbef-0684-ecaa-9e28-3b9e7b6669f2
document_version_independent_id: 6aa7fa8a-692a-94f3-c51d-90fae9628d5c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/importforuser-method-in-class-sms_clientpfxcertificate.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/importforuser-method-in-class-sms_clientpfxcertificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/importforuser-method-in-class-sms_clientpfxcertificate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6c7f0469-4227-c62d-99b9-491d1592299e
---

# ImportForUser Method - Configuration Manager | Microsoft Learn

The `ImportForUser` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports a certificate for a user, encrypted by using a password.

## Syntax

```
sint32 ImportForUser(
     String ProfileName,
     String UserName,
     String EncryptedPfxBlob,
     String Password
);

```

#### Parameters

`ProfileName` Data type: `String`

Qualifiers: [in]

The profile name.

`UserName` Data type: `String`

Qualifiers: [in]

The user name.

`EncryptedPfxBlob` Data type: `String`

Qualifiers: [in]

The encrypted blob.

`Password` Data type: `String`

Qualifiers: [in]

The password used to encrypt the certificate.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).