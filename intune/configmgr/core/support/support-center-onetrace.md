---
layout: Conceptual
title: Support Center OneTrace - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/support-center-onetrace
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
description: OneTrace is a new log viewer with Support Center that has improvements over CMTrace.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ff4d84b2-85a4-bf37-9de2-d612f1e26866
document_version_independent_id: cc4be7ef-7221-c932-d7cc-a4fee5e274a4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/support-center-onetrace.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/support-center-onetrace
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/support-center-onetrace.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 0663307c-db7f-8fad-aab7-1d7862c86a59
---

# Support Center OneTrace - Configuration Manager | Microsoft Learn

OneTrace is a new log viewer with Support Center. It works similarly to CMTrace, with the following improvements:

- A tabbed view
- Dockable windows
- Improved search capabilities
- Ability to enable filters without leaving the log view
- Scrollbar hints to quickly identify clusters of errors
- Fast log opening for large files
- Windows jump lists for recently opened files (version 2103 and later)
- Status messages are displayed in an easy to read format (version 2111 and later)
    - Entries starting with `>>` are status messages that are automatically converted into a readable format when a log is opened. Search or filter on the `>>` string to find status messages in the log.

[![Screenshot of Support Center OneTrace log viewer.](media/3555962-onetrace.png)](media/3555962-onetrace.png#lightbox)

OneTrace works with many types of log files, such as:

- Configuration Manager client logs
- Configuration Manager server logs
- Status messages
- Windows Update ETW log file on Windows 10 or later
- Windows Update log file on Windows 7 & Windows 8.1

## Prerequisites

Starting in version 2107, the all site and client components require .NET version 4.6.2, and version 4.8 is recommended. For more information, [Site and site system prerequisites](../plan-design/configs/site-and-site-system-prerequisites#net-version-requirements).

In version 2103 and earlier, this tool requires .NET 4.6 or later.

## Install

OneTrace installs with Support Center. Find the Support Center installer on the site server at the following path: `cd.latest\SMSSETUP\Tools\SupportCenter\SupportCenterInstaller.msi`.

By default, the OneTrace application is installed at `C:\Program Files (x86)\Configuration Manager Support Center\CMPowerLogViewer.exe`.

Note

Support Center Log File Viewer and OneTrace use Windows Presentation Foundation (WPF). This component isn't available in Windows PE. Continue to use [CMTrace](cmtrace) in boot images with task sequence deployments.

## Log groups

OneTrace supports customizable log groups, similar to the feature in Support Center. Log groups allow you to open all log files for a single scenario. OneTrace currently includes groups for the following scenarios:

- Application management
- Compliance settings (also referred to as Desired Configuration Management)
- Software updates

To show log groups, go to the **View** menu, and select **Log groups**.

![Screenshot of Support Center OneTrace log group for application management.](media/5559993-onetrace-log-groups.png)

### Customize log groups

You can customize these groups by modifying the configuration XML, which by default is in the following path: `C:\Program Files (x86)\Configuration Manager Support Center\LogGroups.xml`.

The following example is one portion of the default configuration file:

```XML
<LogGroups>
  <LogGroup Name="Desired Configuration Management" GroupType="1" GroupFilePath="">
    <LogFile>CIAgent.log</LogFile>
    <LogFile>CIDownloader.log</LogFile>
    <LogFile>CIStateStore.log</LogFile>
    <LogFile>CIStore.log</LogFile>
    <LogFile>CITaskMgr.log</LogFile>
    <LogFile>ccmsdkprovider.log</LogFile>
    <LogFile>DCMAgent.log</LogFile>
    <LogFile>DCMReporting.log</LogFile>
    <LogFile>DcmWmiProvider.log</LogFile>
  </LogGroup>
</LogGroups>
```

The `GroupType` property accepts the following values:

- `0`: Unknown or other
- `1`: Configuration Manager client logs
- `2`: Configuration Manager server logs

The `GroupFilePath` property can include an explicit path for the log files. If it's blank, OneTrace relies upon the registry configuration for the group type. For example, if you set `GroupType=1`, by default OneTrace will automatically look in `C:\Windows\CCM\Logs` for the logs in the group. In this example, you don't need to specify `GroupFilePath`.

## Open recent files

Starting in version 2103, OneTrace supports Windows jump lists for recently opened files. Jump lists let you quickly go to previously opened files, so you can work faster.

There are three methods to open recent files in OneTrace:

- Windows taskbar jump list
- Windows Start menu recently opened list
- In OneTrace from **File** menu or **Recently opened** tab.

### Windows taskbar jump list

When the OneTrace icon is on the Windows taskbar, right-click it, and then select a file from the **Recently opened** list.

![Support Center OneTrace jump list from Windows taskbar with recently opened list.](media/6991505-onetrace-jump-list.png)

### Windows Start menu recently opened list

Go to the **Start** menu, and type `onetrace`. Select a file from the **Recently opened** list.

![Support Center OneTrace in Windows Start menu with recently opened list.](media/6991505-onetrace-start-menu.png)

### OneTrace recently opened list

There are two locations in OneTrace that show the list of recently opened files:

- The **Recently opened** tab in the lower right corner.
- Go to the **File** menu and select a file at the bottom of the menu.

![Support Center OneTrace recently opened lists.](media/6991505-onetrace-recently-opened.png)