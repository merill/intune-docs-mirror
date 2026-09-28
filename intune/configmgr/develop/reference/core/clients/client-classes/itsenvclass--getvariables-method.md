---
layout: Conceptual
title: ITSEnvClass::GetVariables - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--getvariables-method
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
description: In Configuration Manager, the GetVariables method gets the variables for the operating system deployment task sequence environment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5ba7cf78-df9a-f9bf-2634-967d6a2b692b
document_version_independent_id: 34b3bc14-28c7-2abf-1f33-7fda8a91c894
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--getvariables-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/itsenvclass--getvariables-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--getvariables-method.md
cmProducts: []
platformId: 0f3a2773-f04d-d49b-7272-aa15fe3a5f3c
---

# ITSEnvClass::GetVariables - Configuration Manager | Microsoft Learn

In Configuration Manager, the `GetVariables` method gets the variables for the operating system deployment task sequence environment.

## Syntax

```
[IDL]
HRESULT GetVariables(
     VARIANT* variables
);
```

#### Parameters

`variables` Data type: `VARIANT`

Qualifiers: [out, retval]

Pointer to the environment variables.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following value.

S\_OK The method succeeded.