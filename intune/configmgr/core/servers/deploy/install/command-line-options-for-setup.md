---
layout: Conceptual
title: Setup command-line options - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/command-line-options-for-setup
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
description: Create automation scripts to install Configuration Manager from a command line.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e974688b-b85e-3698-7b8e-6ed3396f0267
document_version_independent_id: f6853905-1140-5336-e469-a61c86b1e49e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/command-line-options-for-setup.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/command-line-options-for-setup
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/command-line-options-for-setup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 867e293e-2891-57e6-5686-8b8f326c284b
---

# Setup command-line options - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use this information to configure scripts or to install Configuration Manager from a command line. For more information on how to use these command-line options, see [Command-line overview](use-a-command-line-to-install-sites).

Run `setup.exe` from the `\BIN\X64` directory of the Configuration Manager installation path on the site server.

Tip

You can also use `setupwpf.exe` from the same folder, but it doesn't include basic prerequisite checks.

## `/DEINSTALL`

Uninstall the site. Run setup from the site server computer.

## `/DONTSTARTSITECOMP`

Install a site, but prevent the Site Component Manager service from starting. Until the Site Component Manager service starts, the site isn't active. The Site Component Manager is responsible for installing and starting the SMS\_Executive service, and for other processes at the site. After the site install is finished, when you start the Site Component Manager service, it installs the SMS\_Executive service and other processes that are necessary for the site to operate.

## `/HIDDEN`

Hide the user interface during setup. Only use this option with the `/SCRIPT` option. The unattended script file must provide all required options or setup fails.

## `/NOUSERINPUT`

Disable user input during setup, but display the setup wizard. Only use this option with the `/SCRIPT` option. The unattended script file must provide all required options or setup fails.

## `/RESETSITE`

Run a site reset. This action resets the database and service accounts for the site. For more information, see [Run a site reset](../../manage/modify-your-infrastructure#bkmk_reset).

## `/SQLMOVE`

Move the site database. This action moves the site database to a new instance of SQL Server on the same computer, or to a different computer that runs a supported version of SQL Server. For more information, see [Modify the site database configuration](../../manage/modify-your-infrastructure#bkmk_dbconfig).

Provide the SQL server name, database name and instance name in the following format:

`/SQLMOVE <SQL Server FQDN>:<Database Name>:<SSB Port>`

`/SQLMOVE <SQL Server FQDN>:<InstanceName>\<Database Name>:<SSB Port>`

## `/TESTDBUPGRADE`

Run a test on a backup of the site database to make sure that the database can upgrade.

Important

The test upgrade is no longer a required or recommend step for most sites.

If your database is suspect, or is modified by customizations not explicitly supported by Configuration Manager, continue to use this process.

Don't run this command-line option on your production site database. Running this command-line option on your production site database upgrades the site database and could render your site inoperable.

Provide the instance name and database name for the site database. If you specify only the database name, setup uses the default instance name.

`/TESTDBUPGRADE <Instance name>\<Database name>`

`/TESTDBUPGRADE CM_ABC`

`/TESTDBUPGRADE Named\CM_ABC`

For more information, see [Test the database upgrade when installing an update](../../manage/test-database-upgrade).

## `/UPGRADE`

Run an unattended upgrade of a site. Specify the product key including the dash (`-`) delimiters. Also specify the path to the previously downloaded setup prerequisite files.

For example: `/UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx C:\Setup\prereqs`

For more information about setup prerequisite files, see [Setup Downloader](setup-downloader).

## `/SCRIPT`

Run an unattended installation. Use a setup initialization file with this option. For more information about how to run setup unattended, see [Install sites using a command line](use-a-command-line-to-install-sites). For more information on the script file keys and values, see [Unattended setup script file keys](command-line-script-file).

For example: `/SCRIPT C:\Setup\setup.ini`

## `/SDKINST`

Install the SMS Provider on the specified server. Provide the fully qualified domain name (FQDN) for the SMS Provider computer. For more information about the SMS Provider, see [Plan for the SMS Provider](../../../plan-design/hierarchy/plan-for-the-sms-provider).

For example: `/SDKINST cm02.contoso.com`

## `/SDKDEINST`

Uninstall the SMS Provider on the specified computer. Provide the FQDN for the SMS Provider computer.

For example: `/SDKDEINST cm01.contoso.com`

## `/MANAGELANGS`

Manage the languages that are installed at a previously installed site. Provide the location for the language script file that contains the language settings. For more information, see the [Keys to manage languages](command-line-script-file#manage-languages).

For example: `/MANAGELANGS C:\Setup\langsetup.ini`