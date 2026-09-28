---
layout: Conceptual
title: Console changes and tips - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-tips
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
description: Learn about changes to the Configuration Manager console and tips for using it.
ms.date: 2024-03-28T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: b7abd33f-b2b5-a194-fcbf-afbd0c9a5430
document_version_independent_id: adf34189-82be-78cb-2db4-3d66fe891a06
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/admin-console-tips.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/admin-console-tips
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/admin-console-tips.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: da9abd10-e2f4-3d2b-48dd-45f417c11f41
---

# Console changes and tips - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the information below to find out about changes to the Configuration Manager console and tips for using the console:

## General tips

### Console improvements in version 2207

*(Introduced in version 2207)*

The following improvements were made to the console and user experience:

- When using the search bar, the **Path** criteria is added whenever subfolders are included in the search. The **Path** criteria is informational and can't be edited.![Screenshot of search bar with the path criteria.](media/14908615-search-path.png)

### Console improvements in version 2203

*(Introduced in version 2203)*

The following improvements were made to the console and user experience:

- When using temporary device nodes, device actions like **Run Scripts** are now available to make the experience in the console consistent.
- Additional Management Insights rules now have click-through actions
- Copy/paste is available for more objects from details panes.
    - Added the **Name** property in the details pane for configuration items, configuration item related policies, and applications.
- Software update search results and the search criteria are now cached when you navigate to another node. When you navigate back to the **All Software Updates** node, your search criteria and results are preserved from your last query. Closing the console will clear the cached query.
- Added a search filter to the **Products** and **Classifications** tabs in the **Software Update Point Component Properties**.
- You can now exclude subcontainers when doing **Active Directory System Discovery** and **Active Directory User Discovery** in untrusted domains.
- Added a **Cloud Sync** column to collections to indicate if the collection is synchronizing with Microsoft Entra ID.
- Added the **Collection ID** to the collection summary details tab
- Increased the size of the **Membership Rules** pane in the **Properties** page for collections.
- Added a **View Script** option for **Run PowerShell Script** steps when using the **View** action for a task sequence.
- The console now offers a dark theme. For more information, see [How to use the console](admin-console#bkmk_dark).

### Export to CSV

*(Introduced in version 2111)*

Starting in Configuration Manager 2111, you can export the contents of a grid view in the console along with the column headers to a comma-separated values (CSV) file that can be used to import to Excel or other applications. While you could previously cut and paste from a grid view, exporting to CSV makes extracting a large number of rows faster and easier. You can export either all or selected items from the following nodes:

- Device Collections
- User Collections
- Devices
- Users

To export the information, select **Export to CSV file** from either the ribbon or the right-click menu. Choose **Export selected items** to only export items you've already selected, or you can choose to **Export all items**.

![Screenshot of the export to csv option in the ribbon of the device collections node.](media/9663857-export-csv.png)

### Enhanced code editor

*(Introduced in version 2107)*

Starting in Configuration Manager 2107, you can edit scripts in an enhanced editor. The new editor supports syntax highlighting, code folding, word wrap, line numbers, and find and replace. The new editor is available in the console wherever scripts and queries can be viewed or edited. The enhanced editor improves the syntax highlighting and code folding that was first introduced in version 2010.

![Screenshot of the new code editor in Configuration Manager](media/8495588-code-editor.png)

Open the new code editor to view or edit scripts and queries from the following locations:

- Configuration item
    - Scripts
    - SQL and WQL queries
    - Detection methods
- Application detection scripts
- Query statement properties
- Create script wizard
- Script properties
- Orchestration group
    - pre-installation scripts
    - post-installation scripts
- Task sequence
    - PowerShell scripts
    - Query WMI option

The new code editor supports the following features:

- Editor mode with syntax highlighting and plain text toggle
- Toggle word wrap and line numbers
- Code folding
- Language selection
- *Find*, *Find and Replace*, and *Go To* line number
- Font type and size selection
- Zoom using buttons or with Ctrl + mouse wheel.
- The information bar at the bottom displays:
    - Number of lines and characters in the script
    - Cursor position
    - If the script is read-only
- Persistent settings across instances for the code window, such as code folding, word wrap, and window size.

### Syntax highlighting for scripting languages

*(Introduced in version 2010)*

To assist you when creating scripts and queries in the Configuration Manager console, you'll now see syntax highlighting and code folding, where available.

[![Syntax highlighting in console](media/7964912-syntax-highlighting.png)](media/7964912-syntax-highlighting.png#lightbox)

#### Supported scripting languages for syntax highlighting

Supported languages for syntax highlighting include PowerShell, JavaScript/JScript, VBScript, and SQL/WQL. The below chart shows which languages are supported for syntax highlighting in each area of the console:

| Console area | PowerShell | VBScript | JavaScript/JScript | SQL/WQL |
| --- | --- | --- | --- | --- |
| Application scripts | Yes | Yes | Yes | - |
| Collection query | - | - | - | Yes |
| Configuration item scripts | Yes | Yes | Yes | Yes |
| Task sequence scripts | Yes | - | - | - |
| Create scripts | Yes | - | - | - |

### Fixed-width font now used in some console areas

*(Introduced in version 2010)*

Various areas in the Configuration Manager console now use the fixed-width font Consolas. This font provides consistent spacing and makes it easier to read. You'll see the Consolas font in the following places:

- Application scripts
- Configuration item scripts
- WMI-based collection membership queries
- CMPivot queries
- Scripts
- Run PowerShell Script
- Run Command Line

[![Script editor example with fixed-width Consolas font](media/7632637-script-editor.png)](media/7632637-script-editor.png#lightbox)

### Shortcuts to status messages

*(Introduced in version 2010)*

You now have an easier way to view status messages for the following objects:

- Devices
- Users
- Content
- Deployments
    - Monitoring workspace
        - Phased deployments (select **Show Deployments** from the Phased Deployments node)
    - Deployments tab in the details pane for:
        - Packages
        - Task sequences

Select one of these objects in the Configuration Manager console, and then select **Show Status Messages** from the ribbon. Set the viewing period, and then the status message viewer opens. The viewer filters the results to the object you selected.

Your user account needs at least **Read** permission to these objects.

For more information, see [Use the status system](use-status-system).

### Improvements to console search

*(Introduced in version 2403)*

We have added a new Global Search bar where users can search from anywhere in the console with an option to quickly see and execute the 5 most recent searches. The default search will now include all workspaces that are when you search to any node in the console, by default, search results will include items from that workspace as well as from all nodes folders and subfolders.

**Global search view**

- Open the console.
- Global Search bar will be visible at the top.
- Enter your string and press enter.
- Search execution will start and you will start seeing the search results.
- Whenever the Search Box is active, you can see a dropdown which contains the Recent Searches with a limit of 5.
- Search should work from all across the console be it any child node, parent node etc.
- Search should also work when switching from Parent Node to child node.
    - Search for any string say "Devices" from any node n1 (Assume n1 is a parent node containing other nodes)
    - Search for any string say "Computer" from any node n2 (Assume n2 is a child node with no node inside it)

![Screenshot showing recent search list of global search box in the CM console.](media/24501008-recentsearch.png)

Note

Recent searches dropdown can be collapsed by clicking outside on the window

**Note:** The path criteria are not editable and they just show the search criteria.

*(Introduced in version 2203)*

- The default search will now include all subfolders. That is when you navigate to any node in the console, by default, search results will include items from that node as well as from all subfolders.
- If you want to search only current node, select the **Current Node** button in the ribbon. The search results will then include items from current node only.
- If you want to search all subfolders, select the **All Subfolders** button in the ribbon. The search results will then include items from current node as well as from all subfolders.

*(Introduced in version 1910)*

- You can use the **All Subfolders** search option from the **Driver Packages** and **Queries** nodes. Starting in version 2002, also use this option from the **Configuration Items** and **Configuration Baselines** nodes.
- When a search returns more than 1,000 results, select the **OK** button on the notice bar to view more results.

    ![Screenshot of notice bar for too many search results](media/4640570-search-too-many-results.png)

    Tip

    The default limit on search results is 1,000. You can change this default value. In the Configuration Manager console, go to the **Search** tab of the ribbon. In the **Options** group, select **Search Settings**. Change the **Search Results** value. A larger number of search results might take longer to display.

    By default, the upper maximum limit is 100,000. To change this limit, set the DWORD value **QueryResultCountMaximum** in the following registry key:

    `HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\AdminUI`

    The in-console setting corresponds to the **QueryResultCountLimit** value in the same key. An administrator can configure these values in the HKLM hive for all users of the device. The HKCU value overrides the HKLM setting.

### Role-based administration for folders

*(Introduced in version 1906)*

You can set security scopes on folders. If you have access to an object in the folder but don't have access to the folder, you'll be unable to see the object. Similarly, if you have access to a folder but not an object within it, you won't see that object. Right-click a folder, choose **Set Security Scopes**, then choose the security scopes you want to apply.

### Views sort by integer values

We've made improvements to how various views sort data. For example, in the **Deployments** node of the **Monitoring** workspace, the following columns now sort as numbers instead of string values:

- Number Errors
- Number In Progress
- Number Other
- Number Success
- Number Unknown

### Move the warning for a large number of results

When you select a node in the console that returns more than 1,000 results, Configuration Manager displays the following warning:

> 
> Configuration Manager returned a large number of results. You can narrow your results by using search. Or, click here to view a maximum of 100000 results.

There's now additional blank space in between this warning and the search field. This move helps to prevent inadvertently selecting the warning to display more results.

### Send feedback

Submit product feedback from the console.

- **Send a smile**: Send feedback on what you liked
- **Send a frown**: Send feedback on what you didn't like
- **Send a suggestion**: Takes you to the product feedback site to share your idea

For more information, see [Product Feedback](../../understand/product-feedback).

## Assets and Compliance workspace

### Co-management Eligible Devices collection

*(Introduced in version 2111)*

There's a new built-in device collection for **Co-management Eligible Devices**. The **Co-management Eligible Devices** collection uses incremental updates and a daily full update to keep the collection up to date.

### Collections tab

*(Introduced in version 2111)*

When you show the members of a device collection, and select a device in the list, switch to the **Collections** tab in the details pane. This new view shows the list of collections of which the selected device is a member. It makes it easier for you to see this information.

![Collections tab in the details pane of the list of collection members.](media/10480635-collections-tab.png)

### Navigate to collection

*(Introduced in version 2107)*

You can now navigate to a collection from the **Collections** tab in the **Devices** node. Select **View Collection** from either the ribbon or the right-click menu in the tab.

![Screenshot of the Collections tab in the Devices node.](media/9502958-collection.png)

### Added maintenance window column

*(Introduced in version 2107)*

A **Maintenance window** column was added to the **Collections** tab in the **Devices** node.

![Screenshot of the Maintenance window column for the Collections tab in the Devices node.](media/9708594-maintenance-window.png)

### Display assigned users

*(Introduced in version 2107)*

If a collection deletion fails due to scope assignment, the assigned users are displayed.

![Screenshot of assigned user list when collection fails to delete due to scope assignment.](media/9709014-assigned-users.png)

### Copy discovery data from the console

*(Introduced in version 2010)*

Copy discovery data from devices and users in the console. Copy the details to the clipboard, or export them all to a file. These actions make it easier for you to quickly get this data from the console. For example, copy the MAC address of a device before you reimage it.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Open the properties for a user or device.
2. On the **General** tab, in the **Discovery data** list, select one or more properties.
3. Right-click the selection, and choose one of the following actions:

    - **Copy value**: Copies just the value. You can also use the keyboard shortcut **Ctrl** + **C**.
    - **Copy property and value**: Copies both the property name and the corresponding value. You can also use the keyboard shortcut **Ctrl** + **Shift** + **C**.
    - **Select all**: Selects all properties and values. You can also use the keyboard shortcut **Ctrl** + **A**.
    - **Save results as**: Saves all properties and values to a comma-separated values (CSV) file that you specify.

[![Screenshot of device properties to copy discovery data](media/6890051-copy-discovery-data.png)](media/6890051-copy-discovery-data.png#lightbox)

### Real-time actions from device lists

*(Introduced in version 1906)*

There are various ways to display a list of devices under the **Devices** node in the **Assets and Compliance** workspace.

- In the **Assets and Compliance** workspace, select the **Device Collections** node. Select a device collection, and choose the action to **Show members**. This action opens a subnode of the **Devices** node with a device list for that collection.

    - When you select the collection subnode, you can now start **CMPivot** from the Collection group of the ribbon.
- In the **Monitoring** workspace, select the **Deployments** node. Select a deployment, and choose the **View Status** action in the ribbon. In the deployment status pane, double-click the total assets to drill-through to a device list.

    - When you select a device in this list, you can now start **CMPivot** and **Run Scripts** from the Device group of the ribbon.

### Collections tab in devices node

*(Introduced in version 1906)*

In the **Assets and Compliance** workspace, go to the **Devices** node, and select a device. In the details pane, switch to the new **Collections** tab. This tab lists the collections that include this device.

Note

This tab currently isn't available from a devices subnode under the **Device Collections** node. For example, when you select the option to **Show Members** on a collection.

This tab may not populate as expected for some users. To see the complete list of collections a device belongs to, you must have the **Full Administrator** security role. This is a known issue. 

### Add SMBIOS GUID column to device and device collection nodes

*(Introduced in version 1906)*

In both the **Devices** and **Device Collections** nodes, you can now add a new column for **SMBIOS GUID**. This value is the same as the **BIOS GUID** property of the System Resource class. It's a unique identifier for the device hardware.

### Search device views using MAC address

You can search for a MAC address in a device view of the Configuration Manager console. This property is useful for OS deployment administrators while troubleshooting PXE-based deployments. When you view a list of devices, add the **MAC Address** column to the view. Use the search field to add the **MAC Address** search criteria.

### View users for a device

The following columns are available in the **Devices** node:

- **Primary user(s)**
- **Currently logged on user**

    Note

    Viewing the currently logged on user requires [user discovery](../deploy/configure/configure-discovery-methods#bkmk_config-adud) and [user device affinity](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity).

For more information on how to show a non-default column, see [How to use the admin console](admin-console#columns).

### Improvement to device search performance

When searching in a device collection, it doesn't search the keyword against all object properties. When you're not specific about what to search, it searches across the following four properties:

- Name
- Primary user(s)
- Currently logged on user
- Last logon user name

This behavior significantly improves the time it takes to search by name, especially in a large environment. Custom searches by specific criteria are unaffected by this change.

## Software Library workspace

### Folder support for software update nodes

*(Introduced in version 2203)*

You can organize software update groups and packages by using folders. This change allows for better categorization and management of software updates. For more information, see [Deploy software updates](../../../sum/deploy-use/deploy-software-updates#bkmk_folder).

### Improvements to console search

*(Introduced in version 2107)*

You can use the **All Subfolders** search option for the following nodes:

- **Boot Images** node
- **Operating System Upgrade Packages** node
- **Operating System Images** node

### Run software updates evaluation from deployment status

*(Introduced in version 2107)*

You can right-click and notify devices to run a software updates evaluation cycle from the [software update deployment status](../../../sum/deploy-use/monitor-software-updates#BKMK_SUDeployStatus). You can target a single device under the **Asset Details** pane or select a group of devices based on their deployment status.

![Screenshot of the right-click action for software updates deployment evaluation from the software update deployment status](media/9012080-run-software-update-deployment-evaluation.png)

1. In the Configuration Manager console, navigate to **Monitoring** &gt; **Overview** &gt; **Deployments**.
2. Select the software update group or software update for which you want to monitor the deployment status.
3. On the Home tab, in the Deployment group, select **View Status**.
4. Right-click on either a specific deployment status for the devices, or on a single device under **Asset Details** pane.
5. Select **Evaluate Software Update Deployments** to send a notification to the selected devices to run an evaluation cycle for software update deployments.

### Import objects to current folder

*(Introduced in version 2010)*

When you import an object in the Configuration Manager console, it now imports to the current folder. Previously, Configuration Manager always put imported objects in the root node. This new behavior applies to [applications](../../../apps/deploy-use/import-export-applications), [packages](../../../apps/deploy-use/packages-and-programs), [driver packages](../../../osd/get-started/manage-drivers#driver-packages), and [task sequences](../../../osd/deploy-use/export-import-task-sequences).

### See task sequence size in the console

*(Introduced in version 2010)*

When you view the list of task sequences in the Configuration Manager console, add the **Size (KB)** column. Use this column to identify large task sequences that can cause problems. For more information, see [Reduce the size of task sequence policy](../../../osd/deploy-use/reduce-task-sequence-policy-size).

### Order by program name in task sequence

*(Introduced in version 1906)*

In the **Software Library** workspace, expand **Operating Systems**, and select the **Task Sequences** node. Edit a task sequence, and select or add the [Install Package](../../../osd/understand/task-sequence-steps#BKMK_InstallPackage) step. If a package has more than one program, the drop-down list now sorts the programs alphabetically.

### Task sequences tab in applications node

*(Introduced in version 1906)*

In the **Software Library** workspace, expand **Application Management**, go to the **Applications** node, and select an application. In the details pane, switch to the new **Task sequences** tab. This tab lists the task sequences that reference this application.

### Drill through required updates

*(Introduced in version 1906)*

1. Go to one of the following places in the Configuration Manager console:

    - **Software Library** &gt; **Software Updates** &gt; **All Software Updates**
    - **Software Library** &gt; **Windows Servicing** &gt; **All Windows Updates**
    - **Software Library** &gt; **Office 365 Client Management** &gt; **Office 365 Updates**
2. Select any update that is required by at least one device.
3. Look at the **Summary** tab and find the pie chart under **Statistics**.
4. Select the **View Required** hyperlink next to the pie chart to drill down into the device list.
5. This action takes you to a temporary node under **Devices** where you can see the devices requiring the update. You can also take actions for the node such as creating a new collection from the list.

Note

Starting on April 21, 2020, Office 365 ProPlus is being renamed to **Microsoft 365 Apps for enterprise**. For more information, see [Name change for Office 365 ProPlus](/en-us/deployoffice/name-change). You may still see references to the old name in the Configuration Manager console and supporting documentation while the console is being updated.

### Maximize the browse registry window

1. In the **Software Library** workspace, expand **Application Management**, and select the **Applications** node.
2. Select an application that has a deployment type with a detection method. For example, a Windows Installer detection method.
3. In the details pane, switch to the **Deployment Types** tab.
4. Open the properties of a deployment type, and switch to the **Detection Method** tab. Select **Add Clause**.
5. Change the **Setting Type** to **Registry** and select **Browse** to open the **Browse Registry** window. You can now maximize this window.

### Edit a task sequence by default

In the **Software Library** workspace, expand **Operating Systems**, and select the **Task Sequences** node. **Edit** is now the default action when opening a task sequence. Previously the default action was **Properties**.

### Go to the collection from an application deployment

1. In the **Software Library** workspace, expand **Application Management**, and select the **Applications** node.
2. Select an application. In the details pane, switch to the **Deployments** tab.
3. Select a deployment, and then choose the new **Collection**option in the ribbon on the Deployment tab. This action switches the view to the collection that's the target of the deployment.
    - This action is also available from the right-click context menu on the deployment in this view.

## Monitoring workspace

### Collection evaluation time

*(Introduced in version 2111)*

When viewing a collection, you could previously see the amount of time the site took to evaluate the collection membership. This data is now also available in the **Monitoring** workspace. When you select a collection in either subnode of the **Collection Evaluation** node, the details pane displays this collection evaluation time data.

![Full Evaluation Status node in the Monitoring workspace of the Configuration Manager console, showing collection evaluation times.](media/9648622-collection-evaluation-data.png)

### Correct names for client operations

*(Introduced in version 1906)*

In the **Monitoring** workspace, select **Client Operations**. The operation to **Switch to next Software Update Point** is now properly named.

### Show collection name for scripts

*(Introduced in version 1906)*

In the **Monitoring** workspace, select the **Script Status** node. It now lists the **Collection Name** and the ID.

### Remove content from monitoring status

1. In the **Monitoring** workspace, expand **Distribution Status**, and select **Content Status**.
2. Select an item in the list, and choose the **View Status** option in the ribbon.
3. In the Asset Details pane, right-click a distribution point, and select the new option **Remove**. This action removes this content from the selected distribution point.

### Copy details in monitoring views

Copy information from the **Asset Details** pane for the following monitoring nodes:

- **Content Distribution Status**
- **Deployment Status**

![Deployment Status view, copy asset details](media/1810-deployment-status.png)

## Administration workspace

### Status message shortcuts

*(Introduced in version 2107)*

Shortcuts to [status messages](use-status-system) were added to the **Administrative Users** node and the **Accounts** node. Select an account, then select **Show Status Messages**.

![Screenshot of Administrative Users node with the Show Status Messages option in the ribbon.](media/8942963-show-status-messages.png)

### Enable some security nodes to use the administration service

Starting in version 1906, you can enable some nodes under the **Security** node to use the administration service. This change allows the console to communicate with the SMS Provider over HTTPS instead of via WMI. For more information, see [Set up the administration service](../../../develop/adminservice/set-up#enable-console-usage).