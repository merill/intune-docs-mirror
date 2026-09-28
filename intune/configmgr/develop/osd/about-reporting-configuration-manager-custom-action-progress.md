---
layout: Conceptual
title: Report Custom Action Progress - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress
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
description: A custom action can report progress information that is used to display a progress indicator.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: f32addc1-a2b2-31d4-c485-db069b7b698c
document_version_independent_id: 826643ce-a911-7d8d-da11-054ccb5900f7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 67bf6fe4-c3fe-7c65-cc28-5ef91a5218e2
---

# Report Custom Action Progress - Configuration Manager | Microsoft Learn

While a custom action is running on a Configuration Manager client, it can report progress information that is used to display a progress indicator.

You use the COM automation interface, [IProgressUI::ShowActionProgress](../reference/core/clients/client-classes/iprogressui--showactionprogress-method), to report progress information to the task sequence environment and to show a progress indicator.

`IProgressUI::ShowActionProgress` is implemented in the COM class, [ProgressUI](../reference/core/clients/client-classes/progressui-client-com-automation-class), which is an out-of-process COM object in TSProgressUI.exe.

## ProgressUI in the Task Sequence Environment

Before the task sequence runs, `ProgressUI` is registered and then, when the task sequence finishes, it is unregistered. In the source operating system, `ProgressUI` runs under the logged-on user credentials. If no user is logged in when the task sequence runs, the registration for the COM object fails. In the target operating system, and in Windows PE, `ProgressUI` runs under the system account.

## Calling IProgressUI::ShowActionProgress

In your custom action you must do the following to report the progress of your custom action and display a progress indicator.

Note

Typically, you should report progress information if the action takes more than one minute to run.

### Determining Whether the Progress Indicator Should Be Displayed

Using the following logic, you can use environment variables to determine whether the progress indicator should be displayed.

If you are running in WindowsPE ( `_SMSTSInWinPE` == "true"), or

If you are running in full operating system post installation (`_SMSTSReturnToGINA`=="true"), or

If the task sequence is started from media (`_SMSTSLaunchMode` is "CD", "DVD" or "USB"), or

If the task sequence is running in stand-alone mode (`_SMSTSStandAloneMode`=="true"), or

If the show progress UI flag is set (`_SMSTSShowProgressUI` == "true"), the progress indicator should be displayed; otherwise, it should not be displayed.

### Creating the COM ProgressUI Object

You create a `ProgressUI` object by using the same technique that you use with any COM object. In C++ you use `CoCreateInstance`. In C# you add a reference to **SMS TSE Progress UI,** and in your source code you create an instance of the `ProgressUILib.ProgressUIClass` class.

In VBScript, call `CreateObject` with **Microsoft.SMS.TsProgressUI**.

For an example of creating a COM object in VBSript and C#, see [How to Use Task Sequence Variables in a Running Configuration Manager Task Sequence](how-to-specify-the-supported-platforms-for-a-driver).

### Getting the Required Environment Variables

Several environment variables contain information that you must pass to the `IProgressUI::ShowActionProgress` method. For example, the organization name that is needed for the `pszOrgName` parameter is available from the environment variable, `_SMSTSOrgName`. For more information, see [IProgressUI::ShowActionProgress](../reference/core/clients/client-classes/iprogressui--showactionprogress-method). For information about reading task sequence environment variables, see [How to Use Task Sequence Variables in a Running Configuration Manager Task Sequence](how-to-use-task-sequence-variables-in-a-running-task-sequence).

### Calling IProgressUI::ShowActionProgress

Call `IProgressUI::ShowActionProgress` to show the progress indicator by using the information that is retrieved from the environment variables. To pass the current percentage progress, you use the parameters `uActionExecStep` and `uActionExecMaxStep`. For example, if you pass the value 2 in `uActionExecStep` and pass the value 10 in `uActionExecMaxStep`, then the percentage completion of the action is 20 percent.