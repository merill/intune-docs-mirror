---
layout: Conceptual
title: GetSiteADInfo Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getsiteadinfo-method-in-class-sms_site
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
description: Learn how to use the GetSiteADInfo method to get Active Directory information of the site server.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b1d3dfd8-f85b-394c-60fc-392940eb13dd
document_version_independent_id: 0acd3b19-e11e-fdae-695c-0f950835f46a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getsiteadinfo-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getsiteadinfo-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getsiteadinfo-method-in-class-sms_site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 00d4c131-15c2-4e1b-c2cc-6ad0fcdd923c
---

# GetSiteADInfo Method - Configuration Manager | Microsoft Learn

The `GetSiteADInfo` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets Active Directory information of site server.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetSiteADInfo(
   String SiteCode,
   String DCName,
   String DCAddress,
   String DomainName,
   String ForestName,
   String DCSiteName,
   String ClientSiteName
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: [in]

Site code.

`DCName` Data type: `String`

Qualifiers: [out]

Name of the Active Directory domain controller.

`DCAddress` Data type: `String`

Qualifiers: [out]

Domain controller address.

`DomainName` Data type: `String`

Qualifiers: [out]

Domain name.

`ForestName` Data type: `String`

Qualifiers: [out]

Name of the Active Directory forest.

`DCSiteName` Data type: `String`

Qualifiers: [out]

Name of the Active Directory site where the domain controller is located.

`ClientSiteName` Data type: `String`

Qualifiers: [out]

Name of the site that the computer belongs to.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).