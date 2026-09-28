---
layout: Conceptual
title: ITSEnvClass::Value Property - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--value-property
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
description: In Configuration Manager, the Value property contains the value of an operating system deployment task sequence environment variable.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 80c2695d-4e57-c7ad-b847-5a348b13c98c
document_version_independent_id: f15fec4a-cf3b-477a-28fc-f702795e3eb9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--value-property.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/itsenvclass--value-property
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--value-property.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 150012c8-79fb-9c7c-81c9-e6622e9d797b
---

# ITSEnvClass::Value Property - Configuration Manager | Microsoft Learn

In Configuration Manager, the `Value` property contains the value of an operating system deployment task sequence environment variable.

## Syntax

```
[IDL]
HRESULT Value([in] BSTR Name, [in] BSTR Value);

HRESULT Value([in] BSTR Name, [out,retval] BSTR* Value);
```

#### Parameters

`Name` Data type: `BSTR`

Qualifiers: [in]

The name of the environment variable.

`Value` Data type: `BSTR`

Qualifiers: [in; out, retval]

On input, the value to set for the environment variable. On output, this parameter points to the value that is retrieved for the supplied name.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following value.

S\_OK The method succeeded.

## Remarks

The `get_Value` function succeeds with S\_OK when called with an invalid variable name, but retrieves an empty string for the value. This behavior differs from the more common return of a non-zero exit code to indicate an invalid variable name input.