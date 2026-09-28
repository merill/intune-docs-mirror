---
layout: Conceptual
title: CancelDistribution Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/canceldistribution-method-in-class-sms_distributionpoint
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
description: A Windows Management Instrumentation class method that cancels a package distribution.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c5e75ad8-8f27-7845-2f94-5e5896d41b4d
document_version_independent_id: 70039361-361e-fcfc-3886-4bdb6a563cec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/canceldistribution-method-in-class-sms_distributionpoint.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/canceldistribution-method-in-class-sms_distributionpoint
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/canceldistribution-method-in-class-sms_distributionpoint.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae140723-5ea3-48f8-7d73-11cb4ce0c7b2
---

# CancelDistribution Method - Configuration Manager | Microsoft Learn

The `CancelDistribution` Windows Management Instrumentation (WMI) class method, in Configuration Manager, cancels a package distribution. If there's a distribution in-progress for the specified package to the specified distribution point, then calling this method cancels the ongoing distribution and the status of the package distribution will be set to fail for this distribution point.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 CancelDistribution(
     string PackageId,
     string NALPath
);
```

#### Parameters

`PackageId` Data type: `String`

Qualifiers: `[in]`

ID for an existing package.

`NALPath` Data type: `String`

Qualifiers: `[in]`

Network abstraction layer (NAL) path to the distribution point server.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).