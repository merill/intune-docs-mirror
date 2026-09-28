---
layout: Conceptual
title: InitiateUserInstall Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/initiateuserinstall-method-in-class-sms_application
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
description: InitiateUserInstall method is reserved for future use in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3178cba3-3126-126e-1f06-e9052268b6bf
document_version_independent_id: 38320b2a-800f-a8b1-feb9-4376009c3476
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/initiateuserinstall-method-in-class-sms_application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/initiateuserinstall-method-in-class-sms_application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/initiateuserinstall-method-in-class-sms_application.md
cmProducts: []
platformId: 79c476ee-9d5b-a1f6-20b5-e938394725e8
---

# InitiateUserInstall Method - Configuration Manager | Microsoft Learn

Warning

This method is reserved for future use.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 InitiateUserInstall (
     String  ModelName,
     String  Username,
     String  ClientGUID
);

```

#### Parameters

`ModelName` Data type: `String`

Qualifiers: [in]

Model name of the application.

`Username` Data type: `String`

Qualifiers: [in]

Unique user name.

`ClientGUID` Data type: `String`

Qualifiers: [in]

Unique identifier of a client.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).