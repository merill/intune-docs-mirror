---
layout: Conceptual
title: DDRNew - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrnew
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
description: In Configuration Manager, the DDRNew function begins a new data discovery record.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f69f43e4-a5a2-386b-f2da-a21c22d9798b
document_version_independent_id: a95932fe-7ca0-9e24-c136-fa7a0c2f3433
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ddrnew.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ddrnew
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ddrnew.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 97535282-7e00-344f-c088-6e43c7b8cfeb
---

# DDRNew - Configuration Manager | Microsoft Learn

The `DDRNew` function, in Configuration Manager, begins a new data discovery record (DDR).

## Syntax

```
[IDL]
HRESULT DDRNew();
```

#### Parameters

`Architecture` Name of the architecture. The name can refer to an existing or new architecture. The name is used to determine the resource class name. For example, specifying `Car` identifies the `SMS_R_Car` resource class.

`AgentName` Discovery agent that reports the DDR. This name, which should be unique, is added to the `AgentName` property array.

`SiteCode` Site where the resource was discovered. This site name is added to the `AgentSite` property array.

## Return Values

The `DDRNew` function always returns S\_OK.

## Remarks

You must call this function first for each DDR that you create; calling this function begins your DDR.

The `sArchitecture` string is used to identify your resource class name and can take one of the following forms:

- A single word such as Car, which you can use to identify the `SMS_R_Car`resource class.
- A multiword string such as Carpool Inventory, which you can use to identify the `SMS_R_CarpoolInventory` resource class.
- A DMTF-formatted string such as ACME|Car|1.0, which you can use to identify the `SMS_R_ACME_Car_1_0` resource class.
- The string "System" identifies a computer system.

    The agent name, `sAgentName`*,* should always be filled in and should identify the program used to generate the DDR.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).