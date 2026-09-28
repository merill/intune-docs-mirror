---
layout: Conceptual
title: IProgressUI::ShowActionProgress - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showactionprogress-method
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
description: In Configuration Manager, the ShowActionProgress method displays custom action progress information in a dialog box while the custom action is running.
ms.date: 2019-04-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 650871c6-3c98-3eac-9b5d-3617b4879d37
document_version_independent_id: 9883b416-ddef-456a-98c4-2eb8d7c769de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showactionprogress-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iprogressui--showactionprogress-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showactionprogress-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: d7c1fc5b-8ba7-ff60-1d51-826fd3413ee0
---

# IProgressUI::ShowActionProgress - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ShowActionProgress` method displays custom action progress information in a dialog box while the custom action is running.

## Syntax

```
[IDL]
HRESULT ShowActionProgress(
     BSTR pszOrgName,
     BSTR pszTaskSequenceName,
     BSTR pszCustomTitle,
     BSTR pszCurrentAction,
     ULONG uStep,
     ULONG uMaxStep,
     BSTR pszActionExecInfo,
     ULONG uActionExecStep,
     ULONG uActionExecMaxStep
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

Pointer to the text for a custom message that replaces the default title text displayed in the progress dialog box. Pass an empty string if there's no custom message to show. The value can be obtained from the `_SMSTSCustomProgressDialogMessage` environment variable.

#### `pszCurrentAction`

Data type: `BSTR`

Qualifiers: [in]

Pointer to the name of the current task sequence step. The value can be obtained from the `_SMSTSCurrentActionName` environment variable.

#### `uStep`

Data type: `ULONG`

Qualifiers: [in]

The current task sequence step number. The value can be obtained from the `SMSTSNextInstructionPointer` environment variable.

#### `uMaxStep`

Data type: `ULONG`

Qualifiers: [in]

The total number of steps in the task sequence. The value can be obtained from the `_SMSTSInstructionTableSize` environment variable.

#### `pszActionExecInfo`

Data type: `BSTR`

Qualifiers: [in]

Pointer to user-defined, action-specific progress information to be shown in the progress dialog box.

#### `uActionExecStep`

Data type: `ULONG`

Qualifiers: [in]

The numerical step, within the total number of numerical steps, on which the action is currently working.

Use this parameter to determine the percentage of the action that has been completed so far. For more information, see Remarks.

#### `uActionExecMaxStep`

Data type: `ULONG`

Qualifiers: [in]

The total number of numerical steps that the action does.

Use this parameter to determine the percentage of the action that has been completed so far. For more information, see Remarks.

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

## Remarks

The only required information for this method is for the `pszActionExecInfo`, `uActionExecStep`, and `uActionExecMaxStep` parameters. The other parameters can be obtained from the referenced environment variables.

A call to `ShowActionProgress` should specify the percentage completion of the action using the `uActionExecStep` and `uActionExecMaxStep` parameters. For example, if `uActionExecStep` specifies the value 2 and `uActionExecMaxStep` specifies the value 10, the percentage completion of the action is 20 percent.