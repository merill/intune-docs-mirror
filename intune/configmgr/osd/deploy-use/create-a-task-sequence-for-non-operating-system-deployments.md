---
layout: Conceptual
title: Create a task sequence for non-OS deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments
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
description: Create task sequences that aren't for deploying an OS, such as distributing software or automating tasks
ms.date: 2020-11-30T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 4e688f48-d460-38cd-2d17-eece87f9b62c
document_version_independent_id: 8962384c-56e7-165a-46c2-a250a8033dd3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 385bafe2-971c-3adb-fe0d-746eddda7345
---

# Create a task sequence for non-OS deployments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Task sequences in Configuration Manager are used to automate different kinds of tasks within your environment. These tasks are primarily designed and tested for deploying operating systems. Configuration Manager has many other features that should be the primary technology that you use for the following scenarios:

- [Application installation](/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management)

    Note

    Starting in version 2002, install complex applications using task sequences via the application model. Add a deployment type to an app that's a task sequence, either to install or uninstall the app. For more information, see [Create Windows applications](../../apps/get-started/creating-windows-applications#bkmk_tsdt).

    Starting in version 2010, use the task sequence deployment type of an application to deploy a task sequence to a user-based collection.
- [Software updates installation](../../sum/understand/software-updates-introduction)
- [Setting configuration](../../compliance/understand/ensure-device-compliance)

Also consider other Microsoft System Center automation technologies, such as [Orchestrator](/en-us/system-center/orchestrator/) and [Service Management Automation](/en-us/system-center/sma/).

The power of task sequences lies in their flexibility and how you use them. They can configure client settings, distribute software, update drivers, edit user states, and do other tasks independent of OS deployment. You can create a custom task sequence to add any number of tasks. The use of custom task sequences for non-OS deployment is supported in Configuration Manager. However, if a task sequence results in unwanted or inconsistent results, look at ways to simplify the operation:

- Use simpler steps
- Divide the actions across multiple task sequences
- Take a phased approach to creating and testing the task sequence

## Supported steps

The following steps are supported for use in a non-OS deployment custom task sequence:

- [Check Readiness](../understand/task-sequence-steps#BKMK_CheckReadiness)
- [Connect To Network Folder](../understand/task-sequence-steps#BKMK_ConnectToNetworkFolder)
- [Download Package Content](../understand/task-sequence-steps#BKMK_DownloadPackageContent)
- [Install Application](../understand/task-sequence-steps#BKMK_InstallApplication)
- [Install Package](../understand/task-sequence-steps#BKMK_InstallPackage)
- [Install Software Updates](../understand/task-sequence-steps#BKMK_InstallSoftwareUpdates)
- [Restart Computer](../understand/task-sequence-steps#BKMK_RestartComputer)
- [Run Command Line](../understand/task-sequence-steps#BKMK_RunCommandLine)
- [Run PowerShell Script](../understand/task-sequence-steps#BKMK_RunPowerShellScript)
- [Run Task Sequence](../understand/task-sequence-steps#child-task-sequence)
- [Set Dynamic Variables](../understand/task-sequence-steps#BKMK_SetDynamicVariables)
- [Set Task Sequence Variable](../understand/task-sequence-steps#BKMK_SetTaskSequenceVariable)