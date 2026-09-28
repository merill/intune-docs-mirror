---
layout: Conceptual
title: GetCIDocuments Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/getcidocuments-method-in-class-sms_application
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
description: Gets all of the configuration item documents for the application installation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a3c0a629-7246-48df-f650-9beb2eaf8bd6
document_version_independent_id: 0037e311-e574-4c75-c4dd-185b4f69dc8e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/getcidocuments-method-in-class-sms_application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/getcidocuments-method-in-class-sms_application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/getcidocuments-method-in-class-sms_application.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 44c7a5ba-3179-af10-c3b7-77e19279d643
---

# GetCIDocuments Method - Configuration Manager | Microsoft Learn

The `GetCIDocuments` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets all of the configuration item documents for the application installation.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 GetCIDocuments (
     uint32  DocCIID[],
     string DocumentID[],
     string DocumentType[]
);
```

#### Parameters

`DocCIID` Data type: `UInt32` Array

Qualifiers: [out]

Configuration item ID of the documents.

`DocumentID` Data type: `String` Array

Qualifiers: [out]

Document ID list.

`DocumentType` Data type: `String` Array

Qualifiers: [out]

Type of document. Possible values are:

| Value | Type of document |
| --- | --- |
| 1 | Represent a manifest document. |
| 2 | Represents a properties document. |
| 3 | Represents a policy document that is the latest version configuration item. |
| -3 | Represents a policy document that is not the latest version configuration item. |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).