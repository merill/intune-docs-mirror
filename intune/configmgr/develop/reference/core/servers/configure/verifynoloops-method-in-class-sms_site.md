---
layout: Conceptual
title: VerifyNoLoops Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/verifynoloops-method-in-class-sms_site
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
description: Learn how to use VerifyNoLoops class method to determine if the insertion of a site in Configuration Manager will result in a recursive loop of the sites.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b4c90d3f-af2e-84dc-9b16-f173acd71c7a
document_version_independent_id: 6f181737-562c-7aad-2903-0c07cdba3b97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/verifynoloops-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/verifynoloops-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/verifynoloops-method-in-class-sms_site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 54f5a838-921a-4e1e-1d96-65f5112732ca
---

# VerifyNoLoops Method - Configuration Manager | Microsoft Learn

The `VerifyNoLoops` Windows Management Instrumentation (WMI) class method, in Configuration Manager, determines if the insertion of a site in the Configuration Manager hierarchy at a specific point will result in a recursive loop of the sites.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 VerifyNoLoops(
     String CentralSiteCode,
     String TargetSiteCode,
     String ParentSiteCode,
     Boolean Result
);
```

#### Parameters

`CentralSiteCode` Data type: `String`

Qualifiers: [in, SizeLimit("3")]

Not used.

`TargetSiteCode` Data type: `String`

Qualifiers: [in, SizeLimit("3")]

Site code of the child site to insert.

`ParentSiteCode` Data type: `String`

Qualifiers: [in, SizeLimit("3")]

Site code of the site that will be the parent of the target site.

`Result` Data type: `Boolean`

Qualifiers: [out]

`true` if no loop is formed by inserting the new site in the Configuration Manager hierarchy

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Example Code

The following example shows how to call the `VerifyNoLoops` method.

```
Dim Site As SWbemObject
Dim NoLoop As Boolean

Set Site = GetObject("winmgmts:root\sms\site_<sitecode>:SMS_Site")
Site.VerifyNoLoops "", "<child sitecode>", "<parent sitecode>", NoLoop

MsgBox "NoLoop = " & NoLoop
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).