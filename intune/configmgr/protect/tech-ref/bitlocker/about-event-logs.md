---
layout: Conceptual
title: BitLocker event logs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/about-event-logs
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
description: Learn about how to work with BitLocker information in the Windows Event Log to troubleshoot problems
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: troubleshooting
ms.collection: tier3
locale: en-us
document_id: 6958f9cc-3d13-0648-6aed-0d4054ad1409
document_version_independent_id: da4984bd-887c-ef9a-3531-b49732cb5249
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/tech-ref/bitlocker/about-event-logs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/tech-ref/bitlocker/about-event-logs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/tech-ref/bitlocker/about-event-logs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6d58bc9-1cbc-639b-4618-a5c955b0fe6e
---

# BitLocker event logs - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The BitLocker management agent and web services use Windows event logs to record messages. In the Event Viewer, go to **Applications and Services Logs**, **Microsoft**, **Windows**. The log channel (node) varies depending upon the computer and the component:

- **MBAM**: BitLocker management agent on a client computer
- **MBAM-Web**:
    - Recovery service on the management point
    - Self-service portal
    - Administration and monitoring website

For more information about specific messages in these logs, see the following articles:

- [Client event logs](client-event-logs)
- [Server event logs](server-event-logs)

In each node, by default you'll see two log channels: **Admin** and **Operational**. For more detailed troubleshooting information, you can also show analytics and debug logs.

## Log properties

In Windows Event Viewer, select a specific log. For example, **Admin**. Go to the **Action** menu, and select **Properties**. Configure the following settings:

- **Maximum log size (KB)**: by default, this setting is `1028` (1 MB) for all logs.
- **When maximum event log size is reached**: by default, the **Admin** and **Operational** logs are set to **Overwrite events as needed (oldest events first)**.

## Analytic and debug logs

You can enable more detailed logs for troubleshooting purposes. In Event Viewer, go to the **View** menu, and select **Show Analytic and Debug Logs**. Now when you browse to the log channel, you'll see two additional logs: **Analytic** and **Debug**.

Tip

By default, these logs have the following properties:

- **Maximum log size (KB)**: `1028` (1 MB)
- **Do not overwrite events (Clear logs manually)**

## Export logs to text

Especially with the analytic and debug logs, you may find it easier to review the logs entries in a single text file. Use the following PowerShell commands to export the event log entries to text files:

```PowerShell
# Out-String with a larger -Width does a better job compared to using Out-File with -Width. -Oldest is only required with debug/analytic logs.

# Debug log
Get-WinEvent -LogName Microsoft-Windows-MBAM/Debug -Oldest | Format-Table -AutoSize | Out-String -Width 4096 | Out-File C:\Temp\MBAM_Log_Debug.txt

# Analytic log
Get-WinEvent -LogName Microsoft-Windows-MBAM/Analytic -Oldest | Format-Table -AutoSize | Out-String -Width 4096 | Out-File C:\Temp\MBAM_Log_Analytic.txt

# Admin log
# The above command truncates the output from the admin log, this sample reformats the strings
Get-WinEvent -LogName Microsoft-Windows-MBAM/Admin |
    Select TimeCreated, LevelDisplayName, TaskDisplayName, @{n='Message';e={$_.Message.trim()}} |
    Format-Table -AutoSize -Wrap | Out-String -Width 4096 |
    Out-File -FilePath C:\Temp\MBAM_Log_Admin.txt
```