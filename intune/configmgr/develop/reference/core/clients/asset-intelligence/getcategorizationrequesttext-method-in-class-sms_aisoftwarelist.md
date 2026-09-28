---
layout: Conceptual
title: GetCategorizationRequestText Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getcategorizationrequesttext-method-in-class-sms_aisoftwarelist
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
description: The GetCategorizationRequestText retrieves the XML that is sent to System Center Online for categorization.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6729a888-e839-c09f-d579-361857c43cac
document_version_independent_id: 6d7dfa9f-8e30-79be-3414-54a91b2af886
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/getcategorizationrequesttext-method-in-class-sms_aisoftwarelist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/getcategorizationrequesttext-method-in-class-sms_aisoftwarelist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/getcategorizationrequesttext-method-in-class-sms_aisoftwarelist.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7d272dac-bbe5-733b-6b7c-fbff5f6c1179
---

# GetCategorizationRequestText Method - Configuration Manager | Microsoft Learn

The `GetCategorizationRequestText` Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves the XML that is sent to System Center Online for categorization.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetCategorizationRequestText(
     String SoftwareKey,
     String CategorizationRequestText
);
```

#### Parameters

`SoftwareKey` Data type: `String`

Qualifiers: [in]

The MD5 hash of the software to be categorized. The hash is made up of the software name, publisher, and version.

This property name has changed from `SoftwarePropertiesHash` to `SoftwareKey` in SP1.

`CategorizationRequestText` Data type: `String`

Qualifiers: [out]

XML formatted string which contains the hash, name, version, publisher, evidence type, and system default locale identifier (LCID) of the software.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).