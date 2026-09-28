---
layout: Conceptual
title: Configure remote control - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/configuring-remote-control
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
description: Set up remote control in Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 549ec7fa-5561-466e-afb5-f2d466b0733a
document_version_independent_id: 3af1b35c-7e5d-d964-4f68-20a409511708
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/remote-control/configuring-remote-control.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/remote-control/configuring-remote-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/remote-control/configuring-remote-control.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0dc4d801-c217-e7be-40a8-58856609ad56
---

# Configure remote control - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This procedure describes configuring the default client settings for remote control. These settings apply to all computers in your hierarchy. If you want these settings to apply to only some computers, assign a custom device client setting to a collection that contains those computers. For more information a see [How to configure client settings](../../deploy/configure-client-settings).

To use Remote Assistance or Remote Desktop, it must be installed and configured on the computer that runs the Configuration Manager console. For more information about how to install and configure Remote Assistance or Remote Desktop, see your Windows documentation.

#### To enable remote control and configure client settings

1. In the Configuration Manager console, choose **Administration** &gt; **Client Settings** &gt; **Default Client Settings**.
2. On the **Home** tab, in the **Properties** group, choose **Properties**.
3. In the **Default** dialog box, choose **Remote Tools**.
4. Configure the remote control, Remote Assistance and Remote Desktop client settings. For a list of remote tools client settings that you can configure, see [Remote Tools](../../deploy/about-client-settings#remote-tools).

    You can change the company name that appears in the **ConfigMgr Remote Control** dialog box by configuring a value for **Organization name displayed in Software Center** in the **Computer Agent** client settings.

    Client computers are configured with these settings the next time they download client policy. To initiate policy retrieval for a single client, see [How to manage clients](../manage-clients).

#### Enable keyboard translation

By default, Configuration Manager transmits the key position from the viewer's location to the sharer's location. This can present a problem for keyboard configurations that differ from viewer to sharer. For example, a viewer with an English keyboard would type an "A", but the sharer's French keyboard would provide a "Q". You now have the option of configuring remote control so that the character itself is transmitted from the viewer's keyboard to the sharer, and what the viewer intends to type arrives at the sharer.

To turn on keyboard translation, in **Configuration Manager Remote Control**, choose **Action**,and choose **Enable keyboard translation** to transmit key position.

Note

Special keys, such as ~!#@$%, will not be translated correctly.

## Keyboard shortcuts for the remote control viewer

| Keyboard shortcut | Description |
| --- | --- |
| Alt+Page Up | Switches between running programs from left to right. |
| Alt+Page Down | Switches between running programs from right to left. |
| Alt+Insert | Cycles through running programs in the order that they were opened. |
| Alt+Home | Displays the **Start** menu. |
| Ctrl+Alt+End | Displays the Windows Security dialog box (Ctrl+Alt+Del). |
| Alt+Delete | Displays the Windows menu. |
| Ctrl+Alt+Minus Sign (on the numeric keypad) | Copies the active window of the local computer to the remote computer Clipboard. |
| Ctrl+Alt+Plus Sign (on the numeric keypad) | Copies the entire local computer's window area to the remote computer Clipboard. |