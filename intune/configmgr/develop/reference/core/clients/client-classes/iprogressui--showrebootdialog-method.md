---
layout: Conceptual
title: IProgressUI::ShowRebootDialog - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showrebootdialog-method
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
description: IProgressUI::ShowRebootDialog method
ms.date: 2019-04-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cfc7a6b9-a4da-6232-12a5-45f61797684a
document_version_independent_id: 06aaa411-a288-5f52-efce-38c646e8ed69
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showrebootdialog-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iprogressui--showrebootdialog-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showrebootdialog-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 6295687c-7ab7-15b2-ed6b-c508c79e3c69
---

# IProgressUI::ShowRebootDialog - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ShowRebootDialog` method displays customizable reboot warning dialog box.

## Syntax

```
[IDL]
HRESULT ShowRebootDialog(
     BSTR pszOrgName,
     BSTR pszTaskSequenceName,
     BSTR pszCustomTitle,
     BSTR pszRebootMessage,
     ULONG uErrorCode,
     ULONG uTimeoutInSeconds,
);
```

### Parameters

#### `pszOrgName`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the organization name that's shown in the progress dialog box. The value can be retrieved from the `_SMSTSOrgName` environment variable.

#### `pszTaskSequenceName`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the name of the task sequence that's currently running. The value can be retrieved from the `_SMSTSPackageName` environment variable.

#### `pszCustomTitle`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the text for a custom message that replaces the default title text displayed in the reboot dialog box. Pass an empty string if there's no custom message to show. The value can be obtained from the `_SMSTSCustomProgressDialogMessage` environment variable.

#### `pszRebootMessage`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the text for the custom message that will be displayed in the reboot dialog box. Pass an empty string if there's no custom message to show.

#### `uTimeoutInSeconds`

Data type: `ULONG`

Qualifiers: [in]

Pointer to the value for the number of seconds the dialog box is displayed before closing. The value can be obtained from the `SMSTSErrorDialogTimeout` environment variable, which isn't configured in the task sequence by default. If an empty string is specified for `uTimeoutInSeconds` and `SMSTSErrorDialogTimeout` isn't specified, a default of 900 seconds will be used.

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.