---
layout: Conceptual
title: ClientEditions Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/clienteditions-method-in-class-sms_collection
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
description: Learn how to retrieve a list of client editions and whether the DeviceOwner property may be edited using CLientEditions class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 52bf2572-8be2-b1c1-734a-b526dfc6b06a
document_version_independent_id: 50357f37-ab4f-b34b-2964-15c1b84015af
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/clienteditions-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/clienteditions-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/clienteditions-method-in-class-sms_collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 85abf437-dfc4-4943-821c-d5e536cba444
---

# ClientEditions Method - Configuration Manager | Microsoft Learn

The `ClientEditions` Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves a list of client editions and whether the `DeviceOwner` property may be edited.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ClientEditions(
     UInt32 ClientEdition[],
     Boolean Editable[]
);
```

#### Parameters

`ClientEdition` Data type: `UInt32` Array

Qualifiers: [out]

Edition of the client. Possible values are:

| Value | Client edition |
| --- | --- |
| 0 | Desktop |
| 1 | Windows RT |
| 2 | Windows Mobile 6 |
| 3 | Nokia Symbian |
| 4 | Windows Phone |
| 5 | Mac |
| 6 | Windows CE |
| 7 | Windows Embedded |
| 8 | iOS |
| 9 | iPad |
| 10 | iPodTouch |
| 11 | Andriod |
| 12 | iSocConsumer |
| 13 | Unix/Linux |

`Editable` Data type: `Boolean` Array

Qualifiers: [out]

`true` if the `DeviceOwner` property may be edited.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).