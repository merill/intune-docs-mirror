---
layout: Conceptual
title: User notifications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/user-notifications
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
description: Learn about the configurations to manage notifications to users about application deployments.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 63cc2e0d-6c1b-c00f-e49c-5e151d0105da
document_version_independent_id: d648c7a7-b091-2a84-f9ce-09985d889bbf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/plan-design/user-notifications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/plan-design/user-notifications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/plan-design/user-notifications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: daa3ee2a-344d-3a0f-1737-7af45a85c544
---

# User notifications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Configuration Manager client and Software Center can display notifications to users that are signed-in to Windows. You can control many of these behaviors through client settings and the deployment settings.

Note

By default, Windows 11 enables **focus assist** for the first hour after a user signs on for the first time. For more information, see [Reaching the Desktop and the Quiet Period](/en-us/windows-hardware/customize/desktop/customize-oobe-in-windows-11#reaching-the-desktop-and-the-quiet-period).

Software Center notifications are currently suppressed during this time. For more information, see [Turn Focus assist on or off in Windows](https://support.microsoft.com/windows/turn-focus-assist-on-or-off-in-windows-5492a638-b5a3-1ee0-0c4f-5ae044450e09#ID0EBD=Windows_11).

## Required deployments

When users receive required software, and select the **Snooze and remind me** setting, they can choose from the following options:

- **Later**: Specifies that notifications are scheduled based on the notification settings configured in client settings.
- **Fixed time**: Specifies that the notification is scheduled to display again after the selected time. For example, if you select 30 minutes, the notification displays again in 30 minutes.

![Computer Agent group in default client settings](media/computeragentsettings.png)

The maximum snooze time is always based on the notification values configured in the client settings at every time along the deployment timeline. For example:

- You configure the **Deployment deadline greater than 24 hours, remind users every (hours)** setting on the **Computer Agent** page for 10 hours.
- The client displays the notification dialog more than 24 hours before the deployment deadline.
- The dialog shows snooze options up to but never greater than 10 hours.
- As the deployment deadline approaches, the dialog shows fewer options. These options are consistent with the relevant client settings for each component of the deployment timeline.

For a high-risk deployment, such as a task sequence that deploys an OS, the user notification experience is more intrusive. Instead of a transient taskbar notification, a dialog box like the following displays each time you're notified that critical software maintenance is required:

![Required software dialog notifies you of critical software maintenance](media/client-toast-notification.png)

## Replace toast notifications with dialog window

Sometimes users don't see the Windows toast notification about a restart or required deployment. Then they don't see the experience to snooze the reminder. This behavior can lead to a poor user experience when the client reaches a deadline.

When software changes are required or deployments need a restart, you have the option of using a more intrusive dialog window.

### Software changes are required

When you [deploy an application](../deploy-use/deploy-applications) as required with a deadline in the future, on the **User Experience** page of the Deploy Software Wizard, select the following user notification options:

- **Display in Software Center and show all notifications**
- **When software changes are required, show a dialog window to the user instead of a toast notification**

Configuring this deployment setting changes the user experience for this scenario.

From the following toast notification:

![Toast notification that Software changes are required](media/3555947-required-toast.png)

To the following dialog window:

![Dialog window for Required software changes](media/3555947-required-dialog.png)

### Restart required

In the [Computer Restart](../../core/clients/deploy/about-client-settings#computer-restart) group of client settings, enable the following option: **When a deployment requires a restart, show a dialog window to the user instead of a toast notification**.

Configuring this client setting changes the user experience for all required deployments that require a restart of the following types:

- [Application](../deploy-use/deploy-applications)
- [Task sequence](../../osd/deploy-use/deploy-a-task-sequence)
- [Software update](../../sum/deploy-use/deploy-software-updates)

From the following toast notification:

![Toast notification that Restart required](media/3555947-restart-toast.png)

To the following dialog window:

![Dialog window to Restart your computer](media/3555947-restart-dialog.png)