---
layout: Conceptual
title: Service connection tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/use-the-service-connection-tool
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
description: Learn about this tool that enables you to connect to the Configuration Manager cloud service to manually upload usage information.
ms.date: 2025-03-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 31961974-25bc-92e2-f8fa-08cf4200f05c
document_version_independent_id: fa807068-647a-c18e-8174-6080d6172a07
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/use-the-service-connection-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/use-the-service-connection-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/use-the-service-connection-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 70d4ca3b-1c00-a442-f69b-4a740b6ebcc0
---

# Service connection tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the **service connection tool** when your service connection point is in offline mode. You can also use it when your Configuration Manager site system servers aren't connected to the internet. The tool can help you keep your site up to date with the latest updates to Configuration Manager.

When you run the tool, it connects to the Configuration Manager cloud service, uploads usage information for your hierarchy, and downloads updates. Uploading usage data is necessary to enable the cloud service to provide the correct updates for your environment.

## Prerequisites

- The site has a service connection point, and you configure it for an **Offline, on-demand connection**.
- Run the tool from a command prompt as an administrator. There's no user interface.
- You run the tool from the service connection point and a computer that can connect to the internet. Each of these computers needs to have a x64-bit OS, and have the following components:

    - Both the **Visual C++ Redistributable** x86 and x64 files. By default, Configuration Manager installs the x64 version on the computer that hosts the service connection point. This tool requires the Microsoft Visual C++ 2015-2019 redistributable package (14.28.29914.0), or later, on the computer that you are running it from. To download this component, see [Microsoft Visual C++ Redistributable latest supported downloads](/en-us/cpp/windows/latest-supported-vc-redist).

        Note

        If upgrading from an out of support version of Configuration Manager prior to 2107, the tool requires the Visual C++ 2013 redistributable package (12.0.40660.0), which is available from the same [link](/en-us/cpp/windows/latest-supported-vc-redist).
    - This tool requires .NET version 4.6.2, and version 4.8 is recommended. For more information, see [Site and site system prerequisites](../../plan-design/configs/site-and-site-system-prerequisites).
    - Starting in version 2309, this tool requires installation of the ODBC Driver 18 for SQL Server (x64). To download this component, see [Download ODBC Driver for SQL Server](/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server).
- The account you use to run the tool needs the following permissions:

    - **Local administrator** on the computer that hosts the service connection point
    - **Read** permissions to the site database
- You need a method to transfer the files between the computer with internet access and the service connection point. For example, a USB drive with sufficient free space to store the files and updates.

## Overview

1. **Prepare**: Run the tool on the service connection point. It puts your usage data into a .cab file at the location you specify. Copy the data file to the computer with an internet connection.
2. **Connect**: Run the tool on the computer with an internet connection. It uploads your usage data, and then downloads Configuration Manager updates. Copy the downloaded updates to the service connection point.

    You can upload multiple data files at one time, each from a different hierarchy. You can also specify a proxy server and a user for the proxy server.
3. **Import**: Run the tool on the service connection point. It imports the updates, and adds them to your site. You can then view and [install those updates](install-in-console-updates) in the Configuration Manager console.

### Upload multiple data files

- Put all exported data files from separate hierarchies into the same folder. Give each file a unique name. If necessary, you can manually rename them.
- When you run the tool to upload data to Microsoft, you specify the folder that contains the data files.
- When you run the tool to import data, the tool only imports the data for that hierarchy.

### Specify a proxy server

If the computer with an internet connection requires a proxy server, the tool supports a basic proxy configuration. Use the optional parameters **-proxyserveruri** and **-proxyusername**. For more information, see Command-line parameters.

### Specify the type of updates to download

The tool supports options to control what files you download. By default, the tool downloads only the latest available update that applies to the version of your site. It doesn't download hotfixes.

To modify this behavior, use one of the following parameters to change what files it downloads:

- **-downloadall**: Download all updates, including updates and hotfixes, whatever the version of your site.
- **-downloadhotfix**: Download all hotfixes whatever the version of your site.
- **-downloadsiteversion**: Downloads updates and hotfixes with a later version than the version of your site.

    Important

    Because of a known issue in Configuration Manager version 2002, the default behavior doesn't work as expected. Update to version 2006, or use the **-downloadsiteversion** parameter to download the necessary updates for version 2002.

For more information, see Command-line parameters.

Tip

The tool determines the version of your site from the data file. To verify the version, look in the .cab file for the text file named with the site version.

## Use the tool

The service connection tool is in the Configuration Manager installation media at the following path: `SMSSETUP\TOOLS\ServiceConnectionTool\ServiceConnectionTool.exe`. Always use the service connection tool that matches the version of Configuration Manager that you use. All of these files must be in the same folder for the service connection tool to work.

Copy the **ServiceConnectionTool** folder with all of its contents to the computer with an internet connection.

In this procedure, the command-line examples use the following file names and folder locations. You don't need to use these paths and file names. You can use alternatives that match your environment and preferences.

- The path to the Configuration Manager installation media source files on the service connection point: `C:\Source`
- The path to a USB drive where you store the data to transfer between computers: `D:\USB\`
- The name of the data file that you export from the site: `UsageData.cab`
- The name of the empty folder where the tool stores downloaded updates for Configuration Manager: `UpdatePacks`

### Prepare

1. On the computer that hosts the service connection point, open a command prompt as an administrator, and change directory to the tool location. For example:

    `cd C:\Source\SMSSETUP\TOOLS\ServiceConnectionTool\`
2. Run the following command to prepare the data file:

    `ServiceConnectionTool.exe -prepare -usagedatadest D:\USB\UsageData.cab`

    Note

    If you'll upload data files from more than one hierarchy at the same time, give each data file a unique name. If necessary, you can rename files later.

    The data in the file is based on the level of diagnostic and usage data that you configure for the site. For more information, see [Overview of diagnostics and usage data](../../plan-design/diagnostics/diagnostics-and-usage-data). You can use the tool to export the data to a CSV file to view the contents. For more information, see -export.
3. After the tool finishes exporting the usage data, copy the data file to a computer that has access to the internet.

### Connect

1. On the computer with internet access, open a command prompt as an administrator, and change directory to the tool location. This location is a copy of the entire **ServiceConnectionTool** folder. For example:

    `cd D:\USB\ServiceConnectionTool\`
2. Run the following command to upload the data file and download the Configuration Manager updates:

    `ServiceConnectionTool.exe -connect -usagedatasrc D:\USB -updatepackdest D:\USB\UpdatePacks`

    For more examples, see Command line parameters.

    Note

    When you run this command line, you might see the following error:

    **Unhandled Exception: System.UnauthorizedAccessException: Access to the path 'C:\Users\jqpublic\AppData\Local\Temp\extractmanifestcab\95F8A562.sql' is denied.**

    You can safely ignore this error. Close the error window to continue.
3. After the tool finishes downloading the updates, copy them to the service connection point.

### Import

1. On the computer that hosts the service connection point, open a command prompt as an administrator, and change directory to the tool location. For example:

    `cd C:\Source\SMSSETUP\TOOLS\ServiceConnectionTool\`
2. Run the following command to import the updates:

    `ServiceConnectionTool.exe -import -updatepacksrc D:\USB\UpdatePacks`
3. After the import completes, close the command prompt. It only imports updates for the applicable hierarchy.
4. In the Configuration Manager console, go to the **Administration** workspace, and select the **Updates and Servicing** node. Imported updates are now available to install. For more information, see [Install in-console updates](install-in-console-updates).

## Log files

- **ServiceConnectionTool.log**: Each time you run the service connection tool, it writes to this log file. The path of the log file is always the same location as the tool. This log file provides simple details about the tool usage based on the parameters you use. Each time you run the tool, the tool replaces any existing log file.
- **ConfigMgrSetup.log**: During the Connect phase, the tool writes to this log file at the root of the system drive. This log file provides more detailed information. For example, what files the tool downloads, and if the hash checks are successful.

## Command-line parameters

This section lists in alphabetical order all of the available parameters for the service connection tool.

### -connect

Use during the Connect phase on the computer with internet access. It connects to the Configuration Manager cloud service to upload the data file, and download updates.

It requires the following parameters:

- **-usagedatasrc**: The location of the data file to upload
- **-updatepackdest**: A path for the downloaded updates

You can also use the following optional parameters:

- **-proxyserveruri**: The FQDN of the proxy server
- **-proxyusername**: A user name for the proxy server
- **-downloadall**: Download everything, including updates and hotfixes, whatever the version of your site.
- **-downloadhotfix**: Download all hotfixes, whatever the version of your site.
- **-downloadsiteversion**: Download updates and hotfixes that have a later version than the version of your site.

#### Example of connect without a proxy server

`ServiceConnectionTool.exe -connect -usagedatasrc D:\USB\ -updatepackdest D:\USB\UpdatePacks`

#### Example of connect with a proxy server and port

`ServiceConnectionTool.exe -connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks -proxyserveruri itproxy.contoso.com:8080 -proxyusername jqpublic`

#### Example of connect to download only site version applicable updates

`ServiceConnectionTool.exe -connect -downloadsiteversion -usagedatasrc D:\USB -updatepackdest D:\USB\UpdatePacks`

### -dest

A required parameter with the **-export** parameter to specify the path and file name of the CSV file to export. For more information, see -export.

### -downloadall

An optional parameter with the **-connect** parameter to download everything, including updates and hotfixes, whatever the version of your site. For more information, see -connect.

### -downloadhotfix

An optional parameter with the **-connect** parameter to only download all hotfixes, whatever the version of your site. For more information, see -connect.

### -downloadsiteversion

An optional parameter with the **-connect** parameter to only download updates and hotfixes that have a later version than the version of your site. For more information, see -connect.

### -export

Use during the Prepare phase to export usage data to a CSV file. Run it as an administrator on the service connection point. This action lets you review the contents of the usage data before you upload to Microsoft. It requires the **-dest** parameter to specify the location of the CSV file.

#### Example of export

`-export -dest D:\USB\usagedata.csv`

### -import

Use during the Import phase on the service connection point to import the updates to the site. It requires the **-updatepacksrc** parameter to specify the location of the downloaded updates.

#### Example of import

`ServiceConnectionTool.exe -import -updatepacksrc D:\USB\UpdatePacks`

### -prepare

Use during the Prepare phase on the service connection point to export usage data from the site. It requires the **-usagedatadest** parameter to specify the location of the exported data file.

#### Example of prepare

`ServiceConnectionTool.exe -prepare -usagedatadest D:\USB\UsageData.cab`

### -proxyserveruri

An optional parameter with the **-connect** parameter to specify the FQDN of your proxy server. If your proxy requires a port other than 80 and you fail to specify it, or specify the wrong port, the tool may fail and report with a `CAB does not contain telemetry data.` error. For more information, see -connect.

### -proxyusername

An optional parameter with the **-connect** parameter to specify the username to authenticate with your proxy server. For more information, see -connect.

### -updatepackdest

A required parameter with the **-connect** parameter to specify a path for the downloaded updates. For more information, see -connect.

### -updatepacksrc

A required parameter with the **-import** parameter to specify a path of the downloaded updates. For more information, see -import.

### -usagedatadest

A required parameter with the **-prepare** parameter to specify a path and file name of the exported data file. For more information, see -prepare.