---
layout: Conceptual
title: High-impact task sequence settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/high-impact-task-sequence-settings
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
description: Configure a task sequence as high-impact and customize the messages that users receive when they run the task sequence.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 523cd94f-d007-d521-130d-6d69bfd594bb
document_version_independent_id: 523cd94f-d007-d521-130d-6d69bfd594bb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/high-impact-task-sequence-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/high-impact-task-sequence-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/high-impact-task-sequence-settings.md
cmProducts: []
platformId: 75708b7d-d93a-283d-b335-8b160cb9b85c
---

# High-impact task sequence settings - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configure a task sequence as high-impact and customize the messages that users receive when they run the task sequence. Any task sequence that meets certain conditions is automatically defined as high-impact. For more information, see [Manage high-risk deployments](../../core/servers/manage/settings-to-manage-high-risk-deployments).

Warning

If you use PXE deployments, and configure device hardware with the network adapter as the first boot device, these devices can automatically start an OS deployment task sequence without user interaction. Deployment verification doesn't manage this configuration. While this configuration may simplify the process and reduce user interaction, it puts the device at greater risk for accidental reimage.

## Set a task sequence as high-impact

Use the following procedure to set a task sequence as high-impact.

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and select **Task Sequences**.
2. Select the task sequence to configure, and select **Properties**.
3. On the **User Notification** tab, select **This is a high-impact task sequence**.

## Create a custom notification

Note

The client only displays high-impact notifications for required OS deployment task sequences. It doesn't display them for non-OS deployment or stand-alone task sequences.

Use the following procedure to create a custom notification for high-impact deployments.

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and select **Task Sequences**.
2. Select the task sequence to configure, and select **Properties**.
3. On the **User Notification** tab, select **Use custom text**.

    Note

    You can only set user notification text when you select the option, **This is a high-impact task sequence**.
4. Configure the following settings:

    Note

    Each text box has a maximum limit of 255 characters.

    - **User notification headline text**: Specifies the blue text that displays on the Software Center user notification. For example, in the default user notification, this section contains "Confirm you want to upgrade the operating system on this computer."
    - **User notification message text**: There are three text boxes that provide the body of the custom notification. All text boxes require that you add text.

        - First text box: Specifies the main body of text, typically containing instructions for the user. For example, in the default user notification, this section contains "Upgrading the operating system takes time and your computer might restart several times."
        - Second text box: Specifies the bold text under the main body of text. For example, in the default user notification, this section contains "This in-place upgrade installs the new operating system and automatically migrates your apps, data, and settings."
        - Third text box: Specifies the last line of text under the bold text. For example, in the default user notification, this section contains "Click Install to begin. Otherwise, click Cancel."

## Example

You configure the following custom notification in task sequence properties:

![Customized User Notification tab of task sequence properties.](../media/user-notification.png)

The following notification message displays when the end user opens the installation from Software Center:

![Customized task sequence notification to the end user from Software Center.](../media/user-notification-enduser.png)

Note

If you set up a non-OS deployment task sequence as high-impact, it displays under the Operating Systems node in Software Center as well as all OSD task sequence deployments. Normally, non-OSD task sequence deployments are displayed under the Applications node.