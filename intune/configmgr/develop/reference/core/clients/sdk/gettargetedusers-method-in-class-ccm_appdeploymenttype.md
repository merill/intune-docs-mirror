---
layout: Conceptual
title: GetTargetedUsers Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/gettargetedusers-method-in-class-ccm_appdeploymenttype
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
description: Learn how to retrieve the targeted users of an application deployment type using GetTargetedUsers class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bed7859e-2996-8c70-2cb5-d52f5dd6acea
document_version_independent_id: d460459d-893f-ddd6-bf84-61b9f7060c82
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/gettargetedusers-method-in-class-ccm_appdeploymenttype.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/gettargetedusers-method-in-class-ccm_appdeploymenttype
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/gettargetedusers-method-in-class-ccm_appdeploymenttype.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6ae8d6b2-50c6-f647-08d6-fc94c64f65db
---

# GetTargetedUsers Method - Configuration Manager | Microsoft Learn

The `GetTargetedUsers` Windows Management Instrumentation (WMI) class method in Configuration Manager that retrieves the targeted users of an application deployment type.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetTargetedUsers
{
    [IN]    String Id
    [IN]    String Revision
    [OUT]   String Users[]
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: [id("0"), in]

Identifier.

`Revision` Data type: `String`

Qualifiers: [id("1"), in]

Revision.

`Users` Data type: `String Array`

Qualifiers: [id("2"), out]

Targeted users.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).