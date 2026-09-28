---
layout: Conceptual
title: Install console - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/install-consoles
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
description: Install the Configuration Manager console to connect to a central administration site or primary site.
ms.date: 2024-12-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4afc0177-a70c-a3e7-b6fb-63284b157020
document_version_independent_id: e255af71-58f9-1086-73aa-736b22c4b8f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/install-consoles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/install-consoles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/install-consoles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: f9df6b97-84ad-25e8-ef7c-654db7c86c5e
---

# Install console - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Administrators use the Configuration Manager console to manage the Configuration Manager environment. Each Configuration Manager console can connect to a central administration site (CAS) or to a primary site. You can't connect a Configuration Manager console to a secondary site.

The Configuration Manager console is always installed on the site server for the CAS or a primary site. To install the console separate from site server installation, run the standalone installer.

## Prerequisites

- [Supported OS versions for Configuration Manager consoles](../../../plan-design/configs/supported-operating-systems-consoles)
- You have local **Administrator** rights on the target computer for the console.
- You have **Read** permissions to the location of the console installation files.

### .NET version requirements

Starting in version 2403, the console requires Microsoft .NET Framework version 4.8. If you install the console on other devices, make sure to update .NET. If the device doesn't already have it, the console setup doesn't install this prerequisite.

Starting in version 2107, the console requires Microsoft .NET Framework version 4.6.2, but version 4.8 is recommended. If you install the console on other devices, make sure to update .NET. If the device doesn't already have it, the console setup doesn't install this prerequisite.

Starting in version 2103, the ConfigurationManager PowerShell module requires Microsoft .NET version 4.7.2 or later.

Note

.NET Framework version 4.6.2 is preinstalled with Windows Server 2016 and Windows 10 version 1607. Later versions of Windows are preinstalled with a later version of the .NET Framework.

.NET Framework version 4.8 isn't supported on some OS versions, such as Windows 10 2015 LTSB.

For more information, see [.NET Framework system requirements](/en-us/dotnet/framework/get-started/system-requirements).

## Source paths

Decide which source path to use:

- ConsoleSetup folder in the installation path on the site server: `\Tools\ConsoleSetup`

    When you install a site server, it copies the console installation files and supported language packs for the site to the **Tools\ConsoleSetup** subfolder. Optionally, you can copy the **ConsoleSetup** folder to an alternate location to start the installation. When you update the site, it always keeps its local version up to date.
- Configuration Manager installation media: `\SMSSETUP\BIN\I386`

    Installing the Configuration Manager console from the installation media always installs the English version. This behavior happens even if the site server supports different languages, or the target computer's OS is set to a different language.

When possible, start the console installer from the **ConsoleSetup** folder rather than from the source media.

Important

Don't install the console using the `CD.Latest` source files. It's an unsupported scenario, and may cause problems with the console installation. For more information, see [The `CD.Latest` folder](../../manage/the-cd.latest-folder#unsupported-scenarios).

If you create a package for installing the console on other computers, make sure the package includes the following files:

- ConsoleSetup.exe
- AdminConsole.msi
- ConfigMgr.AC\_Extension.i386.cab
- ConfigMgr.AC\_Extension.amd64.cab

## Use the Setup Wizard

1. Browse to the source path, and open **ConsoleSetup.exe**.

    Important

    Always install the console by using **ConsoleSetup.exe**. Although you can install the Configuration Manager console by running AdminConsole.msi, this method doesn't run prerequisites or dependency checks. The installation might not install correctly.
2. In the wizard, select **Next**.
3. On the **Site Server** page, enter the fully qualified domain name (FQDN) of the site server to which the Configuration Manager console connects.
4. On the **Installation Folder** page, enter the installation folder for the Configuration Manager console. The folder path can't include trailing spaces or Unicode characters.
5. On the **Ready to Install** page, select **Install**.

## Install from a command prompt

Tip

Installing the Configuration Manager console from a command prompt always installs the English version. This behavior happens even if the target computer's OS is set to a different language. To install the Configuration Manager console in a language other than English, use the Setup Wizard.

### ConsoleSetup.exe command-line options

#### `/q`

Installs the Configuration Manager console unattended. The `TargetDir` and `DefaultSiteServerName` options are required when you use this option.

#### `/uninstall`

Uninstalls the Configuration Manager console. Specify this option first when you use it with the `/q` option.

#### `LangPackDir`

Specifies the path to the folder that contains the language files. You can use **Setup Downloader** to download the language files. If you don't use this option, Setup looks for the language folder in the current folder. If the language folder isn't found, Setup continues to install English only. For more information, see [Setup Downloader](setup-downloader).

#### `TargetDir`

Specifies the installation folder to install the Configuration Manager console. This option is required when you use the `/q` option.

#### `DefaultSiteServerName`

Specifies the FQDN of the site server to which the console connects when it opens. This option is required when you use the `/q` option.

### Examples

#### Silent install

`ConsoleSetup.exe /q "TargetDir=%ProgramFiles%\ConfigMgr Console" DefaultSiteServerName=MyServer.Contoso.com`

#### Silent install with language packs

`ConsoleSetup.exe /q "TargetDir=C:\Program Files\ConfigMgr Console" DefaultSiteServerName=MyServer.Contoso.com LangPackDir=C:\Downloads\ConfigMgr`

#### Silent uninstall

`ConsoleSetup.exe /uninstall /q`

## Postinstallation information

The Configuration Manager console requires installation of the built-in WebView2 extension for certain features such as Community hub and dashboards. A notification to install the extension is given to the console user when they open the console. For more information see, the [WebView2 console extension](../../manage/admin-console-extensions#bkmk_notification).