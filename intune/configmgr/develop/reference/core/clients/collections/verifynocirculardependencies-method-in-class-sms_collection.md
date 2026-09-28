---
layout: Conceptual
title: VerifyNoCircularDependencies Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/verifynocirculardependencies-method-in-class-sms_collection
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
description: Learn how to take two collections as arguments and verify that no circular dependencies form using VerifyNoCircularDependencies.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: acdf912f-c2a5-508f-c863-59b1b4ffff6c
document_version_independent_id: 260f7cc8-66e3-d2a9-89e9-d0de82305867
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/verifynocirculardependencies-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/verifynocirculardependencies-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/verifynocirculardependencies-method-in-class-sms_collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b69e4e31-a175-faad-49a9-edbc781593bd
---

# VerifyNoCircularDependencies Method - Configuration Manager | Microsoft Learn

In Configuration Manager, the `VerifyNoCircularDependencies` Windows Management Instrumentation (WMI) class method takes two collections as arguments and verifies that no circular dependencies would be formed if one collection were the parent of another.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
sint32 VerifyNoCircularDependencies(
        SMS_Collection ref parentCollection,
        SMS_Collection ref subCollection,
        boolean Result);

```

#### Parameters

`parentCollection` Data type: `ref:SMS_Collection`

Qualifiers: [in]

Reference to an [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object path for the parent collection.

`subCollection` Data type: `ref:SMS_Collection`

Qualifiers: [in]

Reference to an [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object path for the child collection.

`Result` Data type: `Boolean`

Qualifiers: [out]

true if there are no circular dependencies, false if there are circular dependencies.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).