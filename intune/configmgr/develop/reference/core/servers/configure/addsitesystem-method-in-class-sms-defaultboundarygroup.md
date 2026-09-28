---
layout: Conceptual
title: AddSiteSystem method in class SMS_DefaultBoundaryGroup - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addsitesystem-method-in-class-sms-defaultboundarygroup
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
ms.date: 2016-03-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how the AddSiteSystem class method adds one or more site system servers to a default boundary group.
locale: en-us
document_id: a2c02a35-dfde-3422-ee30-fa625e760963
document_version_independent_id: 777366b5-9d86-ff0b-b435-1e3bc78eadb0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/addsitesystem-method-in-class-sms-defaultboundarygroup.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/addsitesystem-method-in-class-sms-defaultboundarygroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/addsitesystem-method-in-class-sms-defaultboundarygroup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1afde691-add8-2595-4d41-c5ece8017ec8
---

# AddSiteSystem method in class SMS_DefaultBoundaryGroup - Configuration Manager | Microsoft Learn

The `AddSiteSystem` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds one or more site system servers to a default boundary group.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddSiteSystem(
    String ServerNALPath[],
    UInt32 Flags[]
);
```

### Parameters

`ServerNALPath` Data type: `String` Array

Qualifiers: [in]

Array of network abstraction layer (NAL) paths to one or more site system servers.

`Flags` Data type: `UInt32` Array

Qualifiers: [in]

Specifies the connection type of the boundary. Possible values are:

| Value | Description |
| --- | --- |
| 0 | FAST |
| 1 | SLOW |

Note

This parameter is no longer used for distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).