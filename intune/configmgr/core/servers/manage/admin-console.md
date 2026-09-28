---
layout: Conceptual
title: Configuration Manager console - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console
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
description: Learn about navigating through the Configuration Manager console.
ms.date: 2024-12-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: cef4bca8-634b-87a8-f479-d2e3da8a85c8
document_version_independent_id: ded2670d-c188-f6ef-6852-d41323c04fab
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/admin-console.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/admin-console
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/admin-console.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: c56a7aa9-be1c-ec71-6599-502ef3ef9da5
---

# Configuration Manager console - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Administrators use the Configuration Manager console to manage the Configuration Manager environment. This article covers the fundamentals of navigating the console.

## Open the console

The Configuration Manager console is always installed on every site server. You can also install it on other computers. For more information, see [Install the Configuration Manager console](../deploy/install/install-consoles).

The simplest method to open the console on a Windows computer is to go to **Start** and start typing `Configuration Manager console`. You may not need to type the entire string for Windows to find the best match.

If you browse the Start menu, look for the **Configuration Manager console** icon in the **Microsoft Endpoint Manager** group.

![Microsoft Endpoint Manager start menu icons.](media/microsoft-endpoint-manager-start-menu.png)

## Connect to a site server

The console connects to your central administration site server or to your primary site servers. You can't connect a Configuration Manager console to a secondary site. During installation, you specified the fully qualified domain name (FQDN) of the site server to which the console connects.

To connect to a different site server, use the following steps:

1. Select the arrow at the top of the ribbon, and choose **Connect to a New Site**.

    ![Connect the console to a new site.](media/connect-to-a-new-site.png)
2. Type in the FQDN of the site server. If you've previous session to site server, select the server from the drop-down list.

    ![Site Connection window, enter the FQDN of the site server.](media/site-server-fqdn.png)
3. Select **Connect**.

Tip

You can specify the minimum authentication level for administrators to access Configuration Manager sites. This feature enforces administrators to sign in to Windows with the required level. For more information, see [Plan for the SMS Provider](../../plan-design/hierarchy/plan-for-the-sms-provider#authentication). 

## Navigation

Some areas of the console may not be visible depending on your assigned security role. For more information about roles, see [Fundamentals of role-based administration](../../understand/fundamentals-of-role-based-administration).

### Workspaces

The Configuration Manager console has four **workspaces**:

- **Assets and Compliance**
- **Software Library**
- **Monitoring**
- **Administration**

![Configuration Manager workspaces with context menu.](media/configuration-manager-workspaces.png)

Reorder workspace buttons by selecting the down arrow and choosing **Navigation Pane Options**. Select an item to **Move Up** or **Move Down**. Select **Reset** to restore the default button order.

![Navigation Pane Options window to reorder workspaces.](media/navigation-pane-options.png)

Minimize a workspace button by selecting **Show Fewer Buttons**. The last workspace in the list is minimized first. Select a minimized button and choose **Show More Buttons** to restore the button to its original size.

![Minimized workspaces in the Configuration Manager console.](media/workspace-buttons.png)

### Nodes

Workspaces are a collection of **nodes**. One example of a node is the **Software Update Groups** node in the **Software Library** workspace.

Once you are in the node, you can select the arrow to minimize the navigation pane.

![Example node and highlight minimize arrow.](media/software-update-groups-node.png)

Use the **navigation bar** to move around the console when you minimize the navigation pane.

![Configuration Manager minimized navigation pane.](media/minimized-navigation-pane.png)

In the console, nodes are sometimes organized into folders. When you select the folder, it usually displays a **navigation index** or a **dashboard**.

![Configuration Manager software updates navigation index.](media/software-updates-navigation-index.png)

Note

You can use PowerShell to manage console folders with the following cmdlets:

- [Get-CMFolder](/en-us/powershell/module/configurationmanager/get-cmfolder)
- [New-CMFolder](/en-us/powershell/module/configurationmanager/new-cmfolder)
- [Remove-CMFolder](/en-us/powershell/module/configurationmanager/remove-cmfolder)
- [Set-CMFolder](/en-us/powershell/module/configurationmanager/set-cmfolder)

### Ribbon

The ribbon is at the top of the Configuration Manager console. The ribbon can have more than one tab and can be minimized using the arrow on the right. The buttons on the ribbon change based on the node. Most of the buttons in the ribbon are also available on context menus.

![Example ribbon, highlighting multiple tabs and minimize arrow.](media/ribbon.png)

### Details pane

You can get additional information about items by reviewing the details pane. The details pane can have one or more tabs. The tabs vary depending on the node.

![Configuration Manager example details pane.](media/details-pane.png)

### Columns

You can add, remove, reorder, and resize columns. These actions allow you to display the data you prefer. Available columns vary depending on the node. To add or remove a column from your view, right-click on an existing column heading and select an item. Reorder columns by dragging the column heading where you would like it to be.

![Configuration Managers add column.](media/add-columns.png)

At the bottom of the column context menu, you can sort or group by a column. Additionally, you can sort by a column by selecting its header.

![Configuration Manager group by column.](media/column-group-by.png)

## Reclaim lock for editing objects

If the Configuration Manager console stops responding, you can be locked out of making further changes until the lock expires after 30 minutes. This lock is part of the Configuration Manager SEDO (Serialized Editing of Distributed Objects) system. For more information, see [Configuration Manager SEDO](../../../develop/core/understand/sedo).

You can clear your lock on any object in the Configuration Manager console. This action only applies to your user account that has the lock, and on the same device from which the site granted the lock. When you attempt to access a locked object, you can now **Discard Changes**, and continue editing the object. These changes would be lost anyway when the lock expired.

## View recently connected consoles

You can view the most recent connections for the Configuration Manager console. The view includes active connections and those connections that recently connected. You'll always see your current console connection in the list and you only see connections from the Configuration Manager console. You won't see PowerShell or other SDK-based connections to the SMS Provider. The site removes instances from the list that are older than 30 days.

### Prerequisites to view connected consoles

- Your account needs the **Read** permission on the **SMS\_Site** object.
- Configure the administration service REST API. For more information, see [What is the administration service?](../../../develop/adminservice/overview).

### View connected consoles

1. In the Configuration Manager console, go to the **Administration** workspace.
2. Expand **Security** and select the **Console Connections** node.
3. View the recent connections, with the following properties:

    - User name
    - Machine name
    - Connected site code
    - Console version
    - Last connected time: When the user last *opened* the console
    - An open console in the foreground sends a heartbeat every 10 minutes, which shows in the **Last Console Heartbeat** column.

![View Configuration Manager console connections.](media/console-connections.png)

## Start Microsoft Teams Chat from Console Connections

You can message other Configuration Manager administrators from the **Console Connections** node using Microsoft Teams. When you choose to **Start Microsoft Teams Chat** with an administrator, Microsoft Teams is launched and a chat is opened with the user.

### Prerequisites

- For starting a chat with an administrator, the account you want to chat with needs to have been discovered with [Microsoft Entra ID or AD User Discovery](../deploy/configure/about-discovery-methods#bkmk_aboutUser).
- Microsoft Teams installed on the device from which you run the console. note
- All prerequisites to view connected consoles

### Start Microsoft Teams Chat

1. Go to **Administration** &gt; **Security** &gt; **Console Connections**.
2. Right-click on a user's console connection and select **Start Microsoft Teams Chat**.
    - If the User Principal Name isn't found for the selected administrator, **Start Microsoft Teams Chat** is grayed out.
    - An error message, including a download link, appears if Microsoft Teams isn't installed on the device from which you run the console.
    - If Microsoft Teams is installed on the device from which you run the console, it will open a chat with the user.

### Known issues

The error message notifying you that Microsoft Teams isn't installed won't be displayed if the following Registry key doesn't exist:

Computer\HKEY\_CURRENT\_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

To work around the issue, manually create the Registry key.

## In-console documentation dashboard

The **Documentation** node in the **Community** workspace includes information about Configuration Manager documentation and support articles. It includes the following sections:

- **Recommended**: a manually curated list of important articles.
- **Troubleshooting articles**: guided walkthroughs to assist with troubleshooting Configuration Manager components and features.
- **New and updated support articles**: articles that are recently new or updated.

### Troubleshooting connection errors

The **Documentation** node has no explicit proxy configuration. It uses any OS-defined proxy in the **Internet Options** control panel applet. To retry after a connection error, refresh the **Documentation** node.

## Dark theme for the console

*(Introduced in version 2203)*

Starting in version 2203, the Configuration Manager console offers a dark theme. To use the theme, select the arrow from the top left of the ribbon, then choose **Switch console theme**. Select **Switch console theme** again to return to the light theme. As of version 2303, the main screen of the console and delete secondary site wizards adhere to the dark theme.

![Screenshot of the Configuration Manager using the dark theme for the console. The 'Switch console theme' option is displayed in the upper right corner of the image.](media/9070525-console-dark-theme.png)

### Known issue

- Console restart is required on doing the theme switch, as the node navigation pane might not properly render when you move to a new workspace.
- Currently, there are locations in the console that may not display the dark theme correctly. We are continuously working to improve the dark theme.

## Connect via Windows PowerShell

The Configuration Manager console includes a PowerShell module with over a thousand cmdlets to interact programmatically from the command line. Select the arrow at the top of the ribbon, and choose **Connect via Windows PowerShell**.

For more information, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

## Command-line options

The Configuration Manager console has the following command-line options:

| Option | Description |
| --- | --- |
| `/sms:debugview=1` | A DebugView is included in all ResultViews that specify a view. DebugView shows raw properties (names and values). |
| `/sms:NamespaceView=1` | Shows namespace view in the console. |
| `/sms:ResetSettings` | The console ignores user-persisted connection and view states. The window size isn't reset. |
| `/sms:IgnoreExtensions` | Disables any Configuration Manager extensions. |
| `/sms:NoRestore` | The console ignores previous persisted node navigation. |
| `/server=[ServerName]` | Connect to a CAS or Primary site server by specifying the fully qualified domain name (FQDN) or server name for that site. |