---
layout: Conceptual
title: GetEncryptDecryptKey Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getencryptdecryptkey-method-in-class-sms_statemigration
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
description: The GetEncryptDecryptKey WMI class method retrieves the symmetric key that is used to encrypt and decrypt the user state during state migration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a70da653-fba1-7dcc-56f1-246cf49c04a7
document_version_independent_id: 9ded3975-6e2f-ea65-0fce-ee936f49dbe7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/getencryptdecryptkey-method-in-class-sms_statemigration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/getencryptdecryptkey-method-in-class-sms_statemigration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/getencryptdecryptkey-method-in-class-sms_statemigration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 13ec7783-e0e7-5561-ae5d-1b06760d585e
---

# GetEncryptDecryptKey Method - Configuration Manager | Microsoft Learn

The `GetEncryptDecryptKey` Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves the symmetric key that is used to encrypt and decrypt the user state during state migration.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetEncryptDecryptKey(
   String Key
);
```

#### Parameters

`Key` Data type: `String`

Qualifiers: [out]

The encryption key required to restore user state.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).