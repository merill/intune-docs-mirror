---
layout: Conceptual
title: IProgressUI::ShowMessageEx - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessageex-method
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
description: IProgressUI::ShowMessageEx method
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bfd87586-5b90-596a-aa3a-6e4df7950004
document_version_independent_id: 2519a4a6-6821-b2f6-1d17-2200f6ee03d9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessageex-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessageex-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessageex-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c8700761-d0e1-7c5e-a821-a1a16a16f867
---

# IProgressUI::ShowMessageEx - Configuration Manager | Microsoft Learn

Starting in version 2006, the `ShowMessageEx` method displays a customizable dialog box. This method is similar to the [IProgressUI::ShowMessage](iprogressui--showmessage-method) method, but also includes a new integer result variable, **pResult**.

## Syntax

```
[IDL]
HRESULT ShowMessageEx(
     BSTR pszText,
     BSTR pszCaption,
     ULONG uType,
     INT *pResult
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

#### `pResult`

Data type: `INT`

Qualifiers: [out]

The value of this variable is a standard [Windows message box return value](/en-us/windows/win32/api/winuser/nf-winuser-messagebox#return-value).

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

To evaluate the user's response to the message box, use the pResult parameter.

## Example

The following PowerShell script sample shows how to use this method:

```PowerShell
$Message = "Can you see this message?"
$Title = "Contoso IT"
$Type = 4 # Yes/No
$Output = 0

$TaskSequenceProgressUi = New-Object -ComObject "Microsoft.SMS.TSProgressUI"
$TaskSequenceProgressUi.ShowMessageEx($Message, $Title, $Type, [ref]$Output)

$TSEnv = New-Object -ComObject "Microsoft.SMS.TSEnvironment"
if ($Output -eq 6) {
$TSEnv.Value("TS-UserPressedButton") = 'Yes'
}
```

You can use a script like this in the [Run PowerShell Script](../../../../../osd/understand/task-sequence-steps#BKMK_RunPowerShellScript) step in the task sequence. If the user selects **Yes** in the custom window, the script creates a custom task sequence variable **TS-UserPressedButton** with a value of `Yes`. You can then use this task sequence variable in other scripts or as a condition on other task sequence steps.