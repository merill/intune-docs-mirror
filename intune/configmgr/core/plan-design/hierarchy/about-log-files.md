---
layout: Conceptual
title: About log files - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/about-log-files
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
description: Use log files to troubleshoot issues with Configuration Manager clients and site systems.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 8b4ef525-48be-6f17-1c3e-84d513ca28d9
document_version_independent_id: b85eab81-df13-e438-1298-5953cf149337
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/about-log-files.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/about-log-files
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/about-log-files.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6e0ef063-7e8a-f84d-d556-9f76fc9c5b6f
---

# About log files - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In Configuration Manager, client and site server components record process information in individual log files. You can use the information in these log files to help you troubleshoot issues that might occur. By default, Configuration Manager enables logging for client and server components.

This article provides general information about the Configuration Manager log files. It includes tools to use, how to configure the logs, and where to find them. For more information on specific log files, see [Log files reference](log-files).

## How it works

Most processes in Configuration Manager write operational information to a log file that is dedicated to that process. The log files have `.log` or `.lo_` file extensions. Configuration Manager writes to a `.log` file until that log reaches its maximum size. When the log is full, the `.log` file is copied to a file of the same name but with the `.lo_` extension, and the process or component continues to write to the `.log` file. When the `.log` file again reaches its maximum size, the `.lo_` file is overwritten and the process repeats. Some components establish a log file history by appending a date and time stamp to the log file name and by keeping the `.log` extension.

## Log viewer tools

All Configuration Manager log files are plain text, so you can view them with any text reader like Notepad. The logs use unique formatting that's best viewed with one of the following specialized tools:

- CMTrace
- OneTrace
- Support Center log file viewer

### CMTrace

To view the logs, use the Configuration Manager log viewer tool **CMTrace**. It's located in the `\SMSSetup\Tools` folder of the Configuration Manager source media. The CMTrace tool is added to all boot images that are added to the Software Library. The CMTrace log viewing tool is automatically installed along with the Configuration Manager client. For more information, see [CMTrace](../../support/cmtrace).

### OneTrace

**OneTrace** is a log viewer with Support Center. It works similarly to CMTrace, with improvements. For more information, see [Support Center OneTrace](../../support/support-center-onetrace).

### Support Center Log File Viewer

**Support Center** includes a modern log viewer. This tool replaces CMTrace and provides a customizable interface with support for tabs and dockable windows. It has a fast presentation layer, and can load large log files in seconds. For more information, see [Support Center Log File Viewer](../../support/support-center-ui-reference#support-center-log-file-viewer).

Note

Support Center Log File Viewer and OneTrace use Windows Presentation Foundation (WPF). This component isn't available in Windows PE. Continue to use CMTrace in boot images with task sequence deployments.

## Configure logging options

You can change the configuration of the log files, such as the verbose level, size, and history. There are several ways to change these settings:

- During client installation
- Using Configuration Manager Service Manager
- Using the Windows Registry
- In the Configuration Manager console

You can also use hardware inventory to collect log settings from clients.

### Configure logging options during client installation

You can set the configuration of the client log files during installation. Use the following properties:

- CCMENABLELOGGING
- CCMDEBUGLOGGING
- CCMLOGLEVEL
- CCMLOGMAXHISTORY
- CCMLOGMAXSIZE

For more information, see [Client installation properties](../../clients/deploy/about-client-installation-properties#clientMsiProps).

### Configure logging options by using Configuration Manager Service Manager

You can change where Configuration Manager stores the log files, and their size.

To modify the size of log files, change the name and location of the log file, or to force multiple components to write to a single log file, do the following steps:

#### Modify logging for a component

1. In the Configuration Manager console, go to the **Monitoring** workspace, expand **System Status**, and then select either the **Site Status** or **Component Status** node.
2. In the ribbon, select **Start**, and then select **Configuration Manager Service Manager**.
3. When Configuration Manager Service Manager opens, connect to the site that you want to manage. If the site that you want to manage isn't shown, select **Site**, select **Connect**, and then enter the name of the site server for the correct site.
4. Expand the site and go to **Components** or **Servers**, depending on where the components that you want to manage are located.
5. In the right pane, select one or more components.
6. On the **Component** menu, select **Logging**.
7. In the **Configuration Manager Component Logging** dialog box, complete the available configuration options for your selection.
8. Select **OK** to save the configuration.

### Configure logging options by using the Windows Registry

Use the Windows Registry on the servers or clients to change the following logging options:

- Verbose level
- Maximum history
- Maximum size

When troubleshooting a problem, you can enable verbose logging for Configuration Manager to write additional details in the log files.

Warning

Misconfiguration of these settings can cause Configuration Manager to log large amounts of information, or none at all. While this data can be beneficial for troubleshooting, be cautious when changing these values in production sites. Always test these changes in a lab environment first. Excessive logging can occur, which might make it difficult to find relevant information in the log files.

After you make changes to these registry settings, restart the component:

- If you change the client settings, restart the **SMS Agent Host** service (CcmExec).
- If you change the server settings, restart the **SMS Executive** service.

The registry settings vary depending upon the component:

- Client and management point
- Site server
- Site system role
- Configuration Manager console

#### Client and management point logging options

To configure logging options for all components on a client or management point site system, configure these **REG\_DWORD** values under the following Windows Registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Logging\@Global`

| Name | Values | Description |
| --- | --- | --- |
| LogLevel | `0`: Verbose`1`: Default`2`: Warnings and errors`3`: Errors only | The level of detail to write to log files. |
| LogMaxHistory | Any integer greater than or equal to zero, for example:`0`: No history`1`: Default | When a log file reaches the maximum size, the client renames it as a backup and creates a new log file. Specify how many previous versions to keep. |
| LogMaxSize | Any integer greater than or equal to 10,000, for example:250000 | The maximum log file size in bytes. When a log grows to the specified size, the client renames it as a history file, and creates a new file. The default value is 250,000 bytes. |

Note

Don't change other values that may exist in this registry key.

For advanced debugging, you can also add this **REG\_SZ** value under the following Windows Registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Logging\DebugLogging`

| Name | Values | Description |
| --- | --- | --- |
| Enabled | `True`: enable debug logs`False`: disable debug logs | Enables debug logging for troubleshooting purposes. |

This setting causes the client to log low-level information for troubleshooting. Avoid using this setting in production sites. Excessive logging can occur, which might make it difficult to find relevant information in the log files. Make sure to turn off this setting after you resolve the issue.

#### Site server logging options

You can configure settings globally or for a specific component on the Configuration Manager site server.

Note

The settings in this section don't apply to modern components like `SMS_MESSAGE_PROCESSING_ENGINE` or `SMS_ISVUPDATES_SYNCAGENT`. The later components log names are usually longer than eight characters and may contain underscores.

Configure these values under the following Windows Registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Tracing`

| Name | Values | Type | Description |
| --- | --- | --- | --- |
| SqlEnabled | `1`: enable SQL Server tracing`0`: disable SQL Server tracing | REG\_DWORD | Add SQL Server trace logging to all site server logs. |
| ArchiveEnabled | `1`: enable log archives`0`: disable log archives | REG\_DWORD | Archive site server logs to a separate location for historical preservation. |
| ArchivePath | A valid folder path, for example `C:\Logs\Archive` | REG\_SZ | The path to archive site server logs. |

Only enable SQL Server tracing for troubleshooting purposes. Avoid using it in production sites. Excessive logging can occur, which might make it difficult to find relevant information in the log files. Make sure to turn off this setting after you resolve the issue.

Note

Don't change other values that may exist in this registry key.

To configure logging options for a specific server component, configure these **REG\_DWORD** values under the following Windows Registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Tracing\<ComponentName>`

| Name | Values | Description |
| --- | --- | --- |
| LoggingLevel | `0`: Verbose`1`: Default`2`: Warnings and errors`3`: Errors only | The level of detail to write to log files. |
| LogMaxHistory | Any integer greater than or equal to zero, for example:`0`: No history`1`: Default | When a log file reaches the maximum size, the server renames it as a backup and creates a new log file. Specify how many previous versions to keep. |
| MaxFileSize | Any integer greater than or equal to 10,000, for example:250000 | The maximum log file size in bytes. When a log grows to the specified size, the client renames it as a history file, and creates a new file. The default value is 250,000 bytes. |
| DebugLogging | `1`: enable debug logs`0`: disable debug logs | Enables debug logging for troubleshooting purposes. |

The DebugLogging setting causes the server to log low-level information for troubleshooting. Avoid using this setting in production sites. Excessive logging can occur, which might make it difficult to find relevant information in the log files. Make sure to turn off this setting after you resolve the issue.

Note

Don't change other values that may exist in this registry key.

#### Site system role logging options

You can configure settings globally or for a specific component on a site system that hosts a Configuration Manager server role.

To configure logging options for a specific server component, configure these **REG\_DWORD** values under the following Windows Registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\<ComponentName>\Logging`

For example, for the distribution point role:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP\Logging`

| Name | Values | Description |
| --- | --- | --- |
| LogLevel | `0`: Verbose`1`: Default`2`: Warnings and errors`3`: Errors only | The level of detail to write to log files. |
| LogMaxHistory | Any integer greater than or equal to zero, for example:`0`: No history`1`: Default | When a log file reaches the maximum size, the server renames it as a backup and creates a new log file. Specify how many previous versions to keep. |
| LogMaxSize | Any integer greater than or equal to 10,000, for example:250000 | The maximum log file size in bytes. When a log grows to the specified size, the server renames it as a history file, and creates a new file. The default value is 250,000 bytes. |

Note

Don't change other values that may exist in this registry key.

#### Configuration Manager console logging options

To change the verbose level of the AdminUI.log for the Configuration Manager console, use the following procedure:

1. Open the console configuration file, **Microsoft.ConfigurationManagement.exe.config**, in an XML editor like Notepad. The default configuration file is in the following location: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`
2. Under the **system.diagnostics** &gt; **sources** &gt; **source** element, change the **switchValue** attribute from `Error` to `Verbose`. For example:

    Original: `<source name="SmsAdminUISnapIn" switchValue="Error">` New: `<source name="SmsAdminUISnapIn" switchValue="Verbose" >`
3. Save the file, and restart the console.

### Configure logging options in the Configuration Manager console

Enable or disable verbose logging on a client or collection from the console:

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, select the **Devices** node, and choose a target device.
2. In the ribbon, on the **Home** tab, in the **Device** group, select **Client Diagnostics**. Choose one of the available actions.

For more information, see [Client diagnostics](../../clients/manage/client-notification#client-diagnostics).

### Hardware inventory for client log settings

Starting in version 2107, you can enable hardware inventory to collect client log file settings. Enable the hardware inventory class, **Client Diagnostics (CCM\_ClientDiagnostics)**, and then select the following attributes:

- Debug Logging Enabled
- Logging Enabled
- Log Level
- History File Count
- Max Log File Size

Note

This inventory class isn't enabled by default.

For more information, see [Enable or disable existing hardware inventory classes](../../clients/manage/inventory/extend-hardware-inventory#enable-or-disable-existing-classes).

## Locating log files

Configuration Manager and dependent components store log files in various locations. These locations depend on the process that creates the log file and the configuration of your environment.

The following locations are the defaults. If you customized the installation directories in your environment, the actual paths may vary.

- Client: `C:\Windows\CCM\logs`
- Server: `C:\Program Files\Microsoft Configuration Manager\Logs`
- Management point: `C:\SMS_CCM\Logs`
- Configuration Manager console: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\AdminUILog`
- IIS: `C:\inetpub\logs\logfiles\w3svc1`

### Task sequence log locations

The location of the task sequence log file **smsts.log** varies depending upon the phase of the task sequence:

- In Windows PE before [Format and Partition Disk](../../../osd/understand/task-sequence-steps#BKMK_FormatandPartitionDisk) step: `X:\Windows\temp\smstslog\smsts.log` (X is the Windows PE RAM drive)
- In Windows PE after **Format and Partition Disk** step: `X:\smstslog\smsts.log`, then copied to `C:\_SMSTaskSequence\Logs\smstslog\smsts.log` when drive is ready
- In the new Windows OS before the client is installed: `C:\_SMSTaskSequence\Logs\smstslog\smsts.log`
- In Windows after the client is installed: `C:\Windows\CCM\Logs\smstslog\smsts.log`
- In Windows after the task sequence completes: `C:\Windows\CCM\Logs\smsts.log`

Tip

The read-only task sequence variable [_SMSTSLogPath](../../../osd/understand/task-sequence-variables#SMSTSLogPath) always contains the path of the current log file.