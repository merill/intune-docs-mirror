---
layout: Conceptual
title: SetCategorizationRequest Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/setcategorizationrequest-method-in-class-sms_aisoftwarelist
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
description: In Configuration Manager, the SetCategorizationRequest Windows Management Instrumentation class method initiates a System Center Online software categorization request.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dc30d35c-5bba-716f-30df-aba46759e38f
document_version_independent_id: 60942d4d-8cd4-3ffd-27dc-bd9ca574ba56
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/setcategorizationrequest-method-in-class-sms_aisoftwarelist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/setcategorizationrequest-method-in-class-sms_aisoftwarelist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/setcategorizationrequest-method-in-class-sms_aisoftwarelist.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dc9c6887-79b3-349a-a841-dd58dd01a0ab
---

# SetCategorizationRequest Method - Configuration Manager | Microsoft Learn

The `SetCategorizationRequest` Windows Management Instrumentation (WMI) class method, in Configuration Manager, initiates a System Center Online software categorization request.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 SetCategorizationRequest(
     String SoftwareKey,
);
```

#### Parameters

`SoftwareKey` Data type: `String`

Qualifiers: [in]

Hash of the software to be categorized. After this method is called, the hash is sent to the System Center Online server to be categorized during its next release.

This property name has changed from `SoftwarePropertiesHash` to `SoftwareKey` in SP1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).