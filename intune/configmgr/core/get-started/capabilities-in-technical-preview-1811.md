---
layout: Conceptual
title: Technical preview 1811 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1811
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1811.
ms.date: 2018-12-03T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: d402dc4c-fb60-c377-10e5-2db81dec2fe4
document_version_independent_id: 37730422-c2e6-b7a9-1739-dcf35246bea2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1811.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1811
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1811.md
platformId: 0261e9f7-b2f9-6b22-23ce-da4b278304af
---

# Technical preview 1811 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1811. Install this version to update and add new features to your technical preview site.

Review the [technical preview](technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

**The following sections describe the new features to try out in this version:**

## Don't load Windows PowerShell profiles

You can use Windows PowerShell scripts for detection methods on applications and settings in configuration items. When these scripts run on clients, the Configuration Manager client now calls PowerShell with the `-NoProfile` parameter. This option starts PowerShell without profiles.

A PowerShell profile is a script that runs when PowerShell starts. You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.

Note

This change in behavior doesn't apply to [Scripts](../../apps/deploy-use/create-deploy-scripts) or [CMPivot](../servers/manage/cmpivot). Both of these features already use this PowerShell parameter.

## An Intune connection is no longer required for on-premises MDM

The on-premises MDM prerequisite to configure a Microsoft Intune subscription is no longer required. Your organization still requires Intune licenses to use this feature.

You can now use Configuration Manager to manage Surface Hub devices without requiring an Intune connection.

## Configuration Manager console notifications

To keep you better informed so that you can take the appropriate action, the Configuration Manager console now notifies you for the following events:

- When an update is available for Configuration Manager itself
- When lifecycle and maintenance events occur in the environment

This notification is a bar at the top of the console window below the ribbon. It replaces the previous experience when Configuration Manager updates are available. These in-console notifications still display critical information, but don't interfere with your work in the console. You can't dismiss critical notifications. The console displays all notifications in a new notification area of the title bar.

![Notification bar and flag in console](media/1318035-notify-eval-version-expired.png)

The following notifications are most applicable to the technical preview branch:

- Evaluation version is within 30 days of expiration (Warning): the current date is within 30 days of the expiration date of the evaluation version
- Evaluation version is expired (Critical): the current date is past the expiration date of the evaluation version
- Console version mismatch (Critical): the console version doesn't match the site version
- Site upgrade is available (Warning): there's a new update package available

You can configure each site to show non-critical notifications. In the properties of the site, on the **Alerts** tab, select the option to **Enable console notifications for non-critical site health changes**.

- If you enable this setting, all console users see critical, warning, and information notifications. This setting is enabled by default.
- If you disable this setting, console users only see critical notifications.

Most console notifications are per session. The console evaluates queries when a user launches it. To see changes in the notifications, restart the console. If a user dismisses a non-critical notification, it notifies again when the console restarts if it's still applicable.

The following notifications reevaluate every five minutes:

- Site is in maintenance mode
- Site is in recovery mode
- Site is in upgrade mode

Notifications follow the permissions of role-based administration. For example, if a user doesn't have permissions to see Configuration Manager updates, they won't see those notifications.

Some notifications have a related action. For example, if the console version doesn't match the site version, select **Install the new console version**. This action launches the console installer.

For more information and troubleshooting assistance, see the **SmsAdminUI.log** file on the console computer. By default, this log file is at the following path: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\AdminUILog\SmsAdminUI.log`.

## Improvements to task sequence media creation

These improvements are based on the following feedback:

- Specify drive to cache data for creating task sequence media
- BootMedia Version and PackageID

### Specify temporary storage

When you create task sequence media, now customize the location that the site uses for temporary storage of data. This process can require much temporary drive space. This change gives you greater flexibility to choose where to store these temporary files.

In the **Create Task Sequence Media Wizard**, specify a location for the **Staging folder**. By default this location is similar to the following path: `%UserProfile%\AppData\Local\Temp`.

### Add a label to the media

You can now add a label to task sequence media. This label helps you better identify the media after you create it.

In the **Create Task Sequence Media Wizard**, specify a **Media label**. The default value is `Configuration Manager`. This text field appears in the following locations:

- If you mount an ISO file, Windows displays this label as the name of the mounted drive
- If you format a USB drive, it uses the first 11 characters of the label as its name
- Configuration Manager writes a text file called `MediaLabel.txt` to the root of the media. By default, the file includes a single line of text: `label=Configuration Manager`. If you customize the label for media, this line uses your custom label instead of the default value.

## Improvement to Run PowerShell Script task sequence step

You can now directly enter Windows PowerShell code in the **Run PowerShell Script** step. This change lets you run PowerShell commands during a task sequence without first creating and distributing a package with the script.

![Run PowerShell Script step in sample task sequence](media/1359389-powershell-ts-step.png)