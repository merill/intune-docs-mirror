---
layout: Conceptual
title: IProgressUI interface - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface
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
description: IProgressUI represents the user interface that allows custom actions to report progress to the OS deployment task sequencing environment.
ms.date: 2019-04-03T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d0e72b6d-eb7a-54d3-77ed-de72874dbd47
document_version_independent_id: a9f73167-9808-7e9b-5d52-52a887c7af42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iprogressui-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: b8f29872-0402-10e9-efe4-4ea2317820b8
---

# IProgressUI interface - Configuration Manager | Microsoft Learn

The `IProgressUI` automation interface in Configuration Manager represents the user interface that allows custom actions to report progress to the OS deployment task sequencing environment.

## Methods for this interface

| Term | Definition |
| --- | --- |
| [IProgressUI::CloseProgressDialog](iprogressui--closeprogressdialog-method) | Closes open instances of `IProgressUI` |
| [IProgressUI::ShowActionProgress](iprogressui--showactionprogress-method) | Displays custom action progress information in a dialog box while the custom action is running. |
| [IProgressUI::ShowErrorDialog](iprogressui--showerrordialog-method) | Displays customizable error information in a dialog box. |
| [IProgressUI::ShowMessage](iprogressui--showmessage-method) | Displays customizable dialog box. |
| [IProgressUI::ShowMessageEx](iprogressui--showmessageex-method) | Displays customizable dialog box and captures an integer result variable. |
| [IProgressUI::ShowRebootDialog](iprogressui--showrebootdialog-method) | Displays customizable reboot warning dialog box. |
| [IProgressUI::ShowSwapMediaDialog](iprogressui--showswapmediadialog-method) | Displays message box to prompt a user to swap media. |
| [IProgressUI::ShowTSProgress](iprogressui--showtsprogress-method) | Displays custom task sequence progress information in a dialog box. |

## Remarks

The GUID for `IProgressUI` is B64D758A-01C2-4bf0-9F17-621EFB9CF697.