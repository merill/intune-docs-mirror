---
layout: Conceptual
title: Command-line overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/use-a-command-line-to-install-sites
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
description: Learn how to run Configuration Manager setup at a command prompt for different kinds of site installations.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: ff83b551-08ef-7c2c-a325-40a07d7b28a8
document_version_independent_id: 9c8d28bc-b03a-77eb-d146-6c9392a6e9e2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/use-a-command-line-to-install-sites.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/use-a-command-line-to-install-sites
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/use-a-command-line-to-install-sites.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 91651ec3-e6e1-140f-61a1-a5341f60ffa4
---

# Command-line overview - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can run Configuration Manager setup at a command prompt to automate the installation of different kinds of site types. This article provides an overview of the command-line methods.

## Supported tasks for command-line installations

- Install a central administration site (CAS) or primary site
- Modify the languages in use at a CAS or primary site
- Recovery a site

Tip

You can also install the Configuration Manager client and console from the command prompt. For more information, see the following articles:

- [Install consoles](install-consoles#install-from-a-command-prompt)
- [Deploy clients to Windows computers](../../../clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)

## About the command-line script file

For unattended installations of Configuration Manager, you can specify a script file that contains installation options.

Note

You can't use the unattended script file to upgrade an evaluation site to a licensed installation of Configuration Manager.

To use an answer file with setup, first configure the script file with required keys and values. For an unattended installation of a CAS or primary site, the script file requires the following sections:

- `Identification`
- `Options`
- `SQLConfigOptions`
- `HierarchyExpansionOption`
- `CloudConnectorOptions`
- `SABranchOptions`

Then run setup with the command line-option `/SCRIPT` and specify a script file.

To [recover a site](../../manage/recover-sites#site-recovery-procedures), the script file also uses the RecoveryOptions section.

For a list of keys and values to use in an unattended installation script file, see [Unattended setup script file keys](command-line-script-file).

Note

When you run setup from the [`CD.Latest` folder](../../manage/the-cd.latest-folder) for a scripted install or recovery, include the `CDLatest` key with a value of `1`. This value isn't supported with installation media from the Microsoft Volume License site. For more information on how to use this key name in the script file, see [Command-line options](command-line-options-for-setup).

### Create the script

When you [run setup to install a site using the user interface](use-the-setup-wizard-to-install-sites), setup automatically creates the installation script. When you confirm the settings on the **Summary** page of the wizard, the following actions happen:

- Setup creates the script `%TEMP%\ConfigMgrAutoSave.ini`. You can rename this file before you use it, but it needs the `.ini` file extension.
- The unattended installation script contains the settings that you selected in the wizard.
- You can modify the script to install other sites in your hierarchy.
- You can use this script to do an unattended setup of Configuration Manager.

This script file provides the same information as the Setup Wizard, except that there are no default settings. Specify all values for the setup keys that are required and necessary for your requirements.

When setup creates the unattended installation script, it includes the product key that you entered in the Setup Wizard. This key can be a valid product key, or `EVAL` to install an evaluation version of Configuration Manager. The product key value in the script is required by the prerequisite checker. When setup starts the actual site installation, it clears the product key value in the script. Before using the script for an unattended installation of a new site, edit the script to provide a valid product key or to specify an evaluation installation of Configuration Manager.

Tip

You can also manually create the script file from a plain-text editor like Notepad.

### Section names, key names, and values

The script contains section names, key names, and values.

- Required section key names vary depending on the installation type.
- The order of the sections and the order of the keys within sections aren't important.
- The keys aren't case-sensitive.
- When you provide values for keys, the name of the key must be followed by an equal sign (`=`) and the value for the key. For example, `CDLatest=1`

To view the full set of options, see [Command-line options for setup and scripts](command-line-options-for-setup).

## Use a setup script file

To use a setup script file, specify the file name after the `/SCRIPT` command-line option.

- The script file name requires the `.ini` extension.
- Provide the full path to the file. For example, if you name the file `setup.ini`, and store it in the `C:\Setup` folder, then use the following command line: `setup.exe /script C:\Setup\setup.ini`
- The account that runs setup must have **Administrator** rights on the computer. When you run setup with the unattended script, open the command prompt window with the **Run as administrator** option.

## Modify languages

To modify the languages that are installed at a site from a command prompt:

- Run setup from `<ConfigMgrInstallationPath>\Bin\X64` on the site server
- Use the `/MANAGELANGS` command-line option
- Specify a language script file with the languages to add or remove

For example, use the following command syntax: `setupwpf.exe /MANAGELANGS <language script file>`

For more information values to use in the language script file, see [Manage languages](command-line-script-file#manage-languages).

For more information on languages in Configuration Manager, see [Language packs](language-packs).