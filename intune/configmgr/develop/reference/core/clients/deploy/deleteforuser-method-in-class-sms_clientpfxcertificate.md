---
layout: Conceptual
title: DeleteForUser Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/deleteforuser-method-in-class-sms_clientpfxcertificate
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
description: Article outlining how to delete a certificate for a user with DeleteForUser class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1addb941-47ac-3bfb-d580-4cab52b8e971
document_version_independent_id: c211b626-7658-4318-bedb-3b1fb08cec42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/deleteforuser-method-in-class-sms_clientpfxcertificate.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/deleteforuser-method-in-class-sms_clientpfxcertificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/deleteforuser-method-in-class-sms_clientpfxcertificate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eba41146-848c-2f86-db93-665d6553cf48
---

# DeleteForUser Method - Configuration Manager | Microsoft Learn

The `DeleteForUse` Windows Management Instrumentation (WMI) class method, in Configuration Manager, deletes a certificate for a user.

## Syntax

```
 sint32 DeleteForUser(
     String ProfileName,
     String UserName,
     String Thumbprint
);

```

#### Parameters

`ProfileName` Data type: `String`

Qualifiers: [in]

The profile name.

`UserName` Data type: `String`

Qualifiers: [in]

The user name.

`Thumbprint` Data type: `String`

Qualifiers: [in]

The thumbprint for the certificate.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).