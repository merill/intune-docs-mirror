---
layout: Conceptual
title: GetOnlineCount Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/getonlinecount-method-in-class-sms_cn_clientstatus
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
description: Learn how to get an online count of the selected clients of the target collection using GetOnlineCount class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d4db9290-df09-18ba-ffce-7a12fa1b7f17
document_version_independent_id: b1aa8c9b-19f5-02b0-e6f8-5a9afba84b14
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/status/getonlinecount-method-in-class-sms_cn_clientstatus.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/status/getonlinecount-method-in-class-sms_cn_clientstatus
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/status/getonlinecount-method-in-class-sms_cn_clientstatus.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ce7a735d-9ed3-4101-2f1e-04bb906190f6
---

# GetOnlineCount Method - Configuration Manager | Microsoft Learn

The `GetOnlineCount` Windows Management Instrumentation (WMI) class method, in Configuration Manager, that gets an online count of the selected clients of the target collection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetOnlineCount
{
    [IN]    String TargetCollectionID
    [IN]    Uint32 TargetResourceIDs[]
};
```

## Parameters

`TargetCollectionID` Data type: `String`

Qualifiers: [id("0"), in]

Target collection identifier.

`TargetResourceIDs` Data type: `UInt32` Array

Qualifiers: [id("1"), in]

Target client resource identifiers.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).