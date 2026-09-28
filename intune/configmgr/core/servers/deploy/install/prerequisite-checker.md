---
layout: Conceptual
title: Prerequisite checker - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/prerequisite-checker
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
description: Learn how to use prerequisite checker to identify and fix problems that might block a site or site system role installation.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 9839439a-7e6c-1067-6004-4dbd97f90593
document_version_independent_id: f8d61a3f-a22c-caa7-c796-570f3adbd437
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/prerequisite-checker.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/prerequisite-checker
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/prerequisite-checker.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e733dde-b115-d437-8b31-85a309b948bd
---

# Prerequisite checker - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you run Setup to install or upgrade a Configuration Manager site, or before you install a site system role on a new server, you can use this stand-alone application (**Prereqchk.exe**) from the version of Configuration Manager that you want use to verify server readiness. Use Prerequisite Checker to identify and fix problems that would block a site or site system role installation.

Note

Prerequisite Checker always runs as part of Setup.

By default, when Prerequisite Checker runs:

- It validates the server where it runs.
- The local computer is scanned for an existing site server, and only the checks that are applicable to the site are run.
- If no existing sites are detected, all prerequisite rules are run.
- It checks rules to verify that software and settings required for setup are installed. It's possible that some prerequisites require other configurations or software updates that the tool doesn't check.
- It logs its results in the **ConfigMgrPrereq.log** file on the system drive of the computer. The log file might contain more information that doesn't appear in the tool.

When you run Prerequisite Checker at a command prompt and specify specific command-line options:

- Prerequisite Checker only runs the checks that are associated with the site server or site systems that you specify in the command line.
- To check a remote computer, your user account must have Administrator rights to the remote computer.

For more information, see [List of prerequisite checks](list-of-prerequisite-checks).

## Source folders

By default, the prerequisite checker tool is in one of the following locations:

- `<Configuration Manager installation media>\SMSSETUP\BIN\X64`
- `<Configuration Manager installation path>\BIN\X64`

## Copy to another computer

1. In Windows Explorer, go to one of the `X64` source folders.
2. Copy the following files to the destination folder on the other computer:

    - prereqchk.exe
    - prereqcore.dll
    - prereqchkres.dll This file is in the subfolder for the install language. For example, English is in the `00000409` subfolder.
    - basesql.dll
    - basesvr.dll
    - baseutil.dll

## Run with default checks

1. In Windows Explorer, go to one of the `X64` source folders.
2. Run **prereqchk.exe** to start Prerequisite Checker.

Note

The tool requires administrative permissions on the local computer.

Prerequisite Checker detects existing sites, and if found, runs the checks for upgrade readiness. If no sites are found, it runs all checks. The **Site Type** column provides information about the site server or site system with which the rule is associated.

In the Prerequisite Checker user interface, Prerequisite Checker creates a list of discovered problems in the **Prerequisite result** section.

- Select an item in the list for details about how to resolve the problem.
- Before you install the component, resolve all items in the list that have an **Error** status.
- To review results after you close the tool, open the **ConfigMgrPrereq.log** file in the root of the system drive. The log file might contain more information that's not displayed in the tool.

![Configuration Manager installation prerequisite check tool.](media/prereq-checker.png)

## Run from a command prompt

1. Open a Windows command prompt as an administrator and change directory to one of the `X64` source folders.
2. To start Prerequisite Checker and run all prerequisite checks on the server, run the following command: `prereqchk.exe /LOCAL`

You can also run it with other command-line options. For example, to check a primary site:

`prereqchk.exe /PRI /SQL sql01.contoso.com /SDK cmprov01.contoso.com /JOIN cas.contoso.com /MP mp01.contoso.com /DP dp01.contoso.com`

## Command-line options

There are four installation scenarios. The following list summarizes all of the command-line options for each scenario:

- **Central administration site (CAS)**
    - *Required*
        - `/CAS`
        - `/SDK`
        - `/SQL`
    - *Optional*
        - `/EXPAND`
        - `/INSTALLDIR`
        - `/NOUI`
        - `/SCP`
        - `/SSBPORT`
- **Primary site**
    - *Required*
        - `/PRI`
        - `/SDK`
        - `/SQL`
    - *Optional*
        - `/DP`
        - `/INSTALLDIR`
        - `/JOIN`
        - `/MP`
        - `/NOUI`
        - `/SCP`
        - `/SSBPORT`
- **Secondary site**
    - *Required*
        - `/SEC`
    - *Optional*
        - `/INSTALLDIR`
        - `/INSTALLSQLEXPRESS`
        - `/NOUI`
        - `/SECUPGRADE`
        - `/SOURCEDIR`
        - `/SQLPORT`
        - `/SSBPORT`
- **Configuration Manager console**
    - `/ADMINUI`

For more information on these options, see the following sections.

### `/AdminUI`

*Applies to: Console*

Required. This option verifies that the local computer meets the requirements for installing the Configuration Manager console. It doesn't check any server requirements. You can't combine this option with any other option.

### `/CAS`

*Applies to: CAS*

Required. This option verifies that the local server meets the requirements for the CAS. You can't combine it with the `/PRI` or `/SEC` options.

### `/DP`

*Applies to: Primary*

Optional. Specify the FQDN of the server to host the distribution point role, for example: `/PRI /DP dp01.contoso.com`

This option verifies that the specified server meets the requirements for the distribution point site system role. This option can be used alone or with the `/PRI` option.

### `/Expand`

*Applies to: CAS*

Optional. Specify the FQDN of a primary site, for example: `/CAS /EXPAND cmprimary.contoso.com`

This option verifies that the referenced primary site meets the requirements to expand a hierarchy with a CAS.

### `/InstallDir`

*Applies to: CAS, Primary, Secondary*

Optional. Specify the local installation path, for example `/InstallDir C:\ConfigMgr`

This option verifies the minimum disk space for site installation.

### `/InstallSQLExpress`

*Applies to: Secondary*

Optional. This option verifies that SQL Server Express can be installed on the specified secondary site server.

### `/Join`

*Applies to: Primary*

Optional. Specify the FQDN of the CAS server, for example, `/PRI /JOIN cas.contoso.com`

This option verifies that the local server meets the requirements for connecting to the CAS server.

### `/MP`

*Applies to: Primary*

Optional. Specify the FQDN of the server to host the management point role, for example: `/PRI /MP mp01.contoso.com`

This option verifies that the specified server meets the requirements for the management point site system role. This option can be used alone or with the `/PRI` option.

### `/NoUI`

*Applies to: CAS, Primary, Secondary*

Optional. This option starts the prerequisite checker without displaying the user interface. Specify this option before any other option in the command line.

### `/Pri`

*Applies to: Primary*

Required. This option verifies that the local server meets the requirements for a primary site. You can't combine it with the `/CAS` or `/SEC` options.

### `/SCP`

*Applies to: CAS, Primary*

Optional. Specify the FQDN of the server to host the service connection point. This server may be the same as the site server.

Starting in version 2111, this option verifies that the specified computer meets the requirements for the service connection point site system role. You can use this option alone or with the `/PRI` or `/CAS` options.

### `/SDK`

*Applies to: CAS, Primary*

Required. Specify the FQDN of the server to host the SMS Provider role. This server may be the same as the site server.

This option verifies that the specified server meets the requirements for the SMS Provider.

### `/Sec`

*Applies to: Secondary*

Required. Specify the FQDN of the secondary site server, for example: `/SEC sec01.contoso.com`

This option verifies that the specified server meets the requirements for the secondary site. You can't combine it with the `/CAS` or `/PRI` options.

### `/SecUpgrade`

*Applies to: Secondary*

Optional. Specify the FQDN of the secondary site server, for example: `/SECUPGRADE sec01.contoso.com`

This option verifies that the specified server meets the requirements for the secondary site upgrade. You can't combine it with the `/CAS`, `/PRI`, or `/SEC` options.

### `/SourceDir`

*Applies to: Secondary*

Optional. This option verifies that the computer account of the secondary site can access the folder that hosts the source files for Configuration Manager setup.

### `/SQL`

*Applies to: CAS, Primary*

Required. Specify the fully qualified domain name (FQDN) of the SQL Server, for example `/SQL sql01.contoso.com`

This option verifies that the specified server meets the requirements for SQL Server to host the Configuration Manager site database.

### `/SQLPort`

*Applies to: Secondary*

Optional. This option verifies that a firewall exception exists to allow communication for the SQL Server service port. It also checks that the port isn't in use by another named instance of SQL Server. The default port is 1433.

### `/SSBPort`

*Applies to: CAS, Primary, Secondary*

Optional. This option verifies that a firewall exception exists to allow communication on the SQL Server Service Broker (SSB) port. The default SSB port is 4022.