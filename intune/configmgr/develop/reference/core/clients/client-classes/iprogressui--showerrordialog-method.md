---
layout: Conceptual
title: IProgressUI::ShowErrorDialog - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showerrordialog-method
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
description: IProgressUI::ShowErrorDialog method
ms.date: 2019-04-03T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f733d94e-d04b-d96c-3180-eb8b09a9c568
document_version_independent_id: cccfcc16-d546-31af-b3de-b2b35d933e68
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showerrordialog-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iprogressui--showerrordialog-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showerrordialog-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: cbaeb669-c51e-68c8-9d96-be2f83bab953
---

# IProgressUI::ShowErrorDialog - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ShowErrorDialog` method displays customizable error information in a dialog box.

## Syntax

```
[IDL]
HRESULT ShowErrorDialog(
     BSTR pszOrgName,
     BSTR pszTaskSequenceName,
     BSTR pszCustomTitle,
     BSTR pszErrorMessage,
     ULONG uErrorCode,
     ULONG uTimeoutInSeconds,
     ULONG uWillReboot,
     BSTR pszTaskSequenceStepName
);
```

### Parameters

#### `pszOrgName`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the organization name that is shown in the progress dialog box. The value can be retrieved from the `_SMSTSOrgName` environment variable.

#### `pszTaskSequenceName`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the name of the task sequence that is currently running. The value can be retrieved from the `_SMSTSPackageName` environment variable.

#### `pszCustomTitle`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the text for a custom message that replaces the default title text displayed in the error dialog box. Pass an empty string if there's no custom message to show. The value can be obtained from the `_SMSTSCustomProgressDialogMessage` environment variable.

#### `pszErrorMessage`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the text for the custom message that's displayed in the error dialog box. Pass an empty string if there's no custom message to show. The default text includes the text from `pszTaskSequenceName`, `pszTaskSequenceStepName`, and `uErrorCode`. It changes depending on which values are specified.

#### `uErrorCode`

Data type: `ULONG`

Qualifiers: [in]

Pointer to the return code of the last step that failed. The value can be obtained from the `_SMSTSLastActionRetCode` environment variable. If no custom text for `pszErrorMessage` is specified, `uErrorCode` will be displayed in [Microsoft system error code](/en-us/windows/desktop/debug/system-error-codes) format.

#### `uTimeoutInSeconds`

Data type: `ULONG`

Qualifiers: [in]

Pointer to the value for the number of seconds the dialog box is displayed before closing. The value can be obtained from the `SMSTSErrorDialogTimeout` environment variable, which isn't configured in the task sequence by default. If an empty string is specified for `uTimeoutInSeconds` and `SMSTSErrorDialogTimeout` isn't specified, a default of 900 seconds will be used.

#### `bWillReboot`

Data type: `ULONG`

Qualifiers: [in]

Boolean value. It indicates whether the task sequence will restart the computer when the dialog is closed or the timeout expires.

#### `pszTaskSequenceStepName`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the text for name of the step name that will be displayed in the default `pszErrorMessage` text. The value can be retrieved from the `_SMSTSLastActionName` environment variable.

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.