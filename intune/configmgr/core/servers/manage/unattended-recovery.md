---
layout: Conceptual
title: Unattended recovery - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/unattended-recovery
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
description: Use a script to recover your sites in Configuration Manager.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 7e782ef6-5227-0592-2e9b-edaa762dd48b
document_version_independent_id: 8815c6b1-d4fa-dfad-6efc-f8ac99033609
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/unattended-recovery.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/unattended-recovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/unattended-recovery.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: 26712f3c-f40a-407a-c9c3-0aa1d4baa21c
---

# Unattended recovery - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To recover a Configuration Manager central administration site (CAS) or primary site without user interaction, create an unattended installation script to use with the `/script` setup command-line option. The script provides the same type of information that the setup wizard prompts for, except that there are no default settings. Specify all values for the setup keys that apply to the type of recovery.

To use the `/script` setup command-line option, first create an answer file. Then specify this file name on the command line. The name of the file is your decision, but it requires the `.ini` file extension. When you reference this answer file from the command line, provide the full path to the file. For example, if your setup answer file is named `setup.ini`, and it's stored in the `C:\setup` folder, your command line would be:

`setup.exe /script c:\setup\setup.ini`

Important

You need **Administrator** rights to run Configuration Manager setup. When you run setup with the unattended script, open the command prompt with the option to **Run as administrator**.

The script contains section names, key names, and values. Required section key names vary depending on the recovery type that you need. The order of the keys within sections and the order of sections within the file aren't important. The keys aren't case-sensitive. When you provide values for keys, the name of the key is followed by an equal sign (`=`) and the value for the key. For example, `Action=RecoverCCAR`.

For more information, see the following articles:

[Command-line options for setup](../deploy/install/command-line-options-for-setup)

[Unattended setup script file keys](../deploy/install/command-line-script-file)