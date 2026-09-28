---
layout: Conceptual
title: IProgressUI::ShowMessage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessage-method
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
description: IProgressUI::ShowMessage method
ms.date: 2019-04-03T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 454310eb-79ce-0a08-551b-1648b404fdcf
document_version_independent_id: 7594953d-3825-0225-89a4-f7f394e894c6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessage-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessage-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessage-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 717f6623-d43c-c137-37ca-8746472185a6
---

# IProgressUI::ShowMessage - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ShowMessage` method displays customizable dialog box.

## Syntax

```
[IDL]
HRESULT ShowMessage(
     BSTR pszText,
     BSTR pszCaption,
     ULONG uType
);
```

### Parameters

#### `pszText`

Data type: `BSTR`

Qualifiers: [in]

The text displayed in the message box body.

#### `pszCaption`

Data type: `BSTR`

Qualifiers: [in]

The text displayed in the message box windows header.

#### `uType`

Data type: `ULONG`

Qualifiers: [in]

The value corresponding to one of the following possible values for the buttons:

- 0 - Ok
- 1 - Ok/Cancel
- 2 - Abort/Retry/Ignore
- 3 - Yes/No/Cancel
- 4 - Yes/No
- 5 - Retry/Cancel
- 6 - Cancel/Try Again/Continue

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

To evaluate the user's response to the message box, use the [IProgressUI::ShowMessageEx](iprogressui--showmessageex-method) method.