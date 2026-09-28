---
layout: Conceptual
title: Technical preview 2110 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2110
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2110.
ms.date: 2021-10-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 022c9a49-3d97-1ecb-99d1-99626160d8ad
document_version_independent_id: 1089b01c-b12c-0778-e865-4f57a5ae5365
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2110.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2110
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2110.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
platformId: 21bb4e31-4ec3-07de-ac6f-f0be68331b50
---

# Technical preview 2110 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2110. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Simplified cloud attach configuration

We've simplified the process to cloud attach your Configuration Manager environment. You can now choose to use a streamlined set of recommended defaults when cloud attaching your environment. By using the recommended default settings, your eligible devices will be cloud attached and you'll enable capabilities like rich analytics, cloud console, and real-time device querying. The default settings include the following features:

- Enables automatic enrollment of all eligible devices into Intune
    - Enrolls your clients into [co-management](../../../comanage/tutorial-co-manage-clients), with all [workloads](../../../comanage/workloads) pointed to Configuration Manager
- Enables [Endpoint analytics](../../../../endpoint-analytics/scores)
- Enables automatic upload of all your devices to Microsoft Intune admin center ([tenant attach](../../../tenant-attach/device-sync-actions))

![Screenshot of the cloud attach configuration wizard](media/10964629-cloud-attach-wizard.png)

### Cloud attach using the default settings

Use the following steps to cloud attach your environment with the default settings:

1. From the Configuration Manager console, go to **Administration** &gt; **Cloud services** &gt; **Cloud Attach**.
2. Select **Configure Cloud Attach** from the ribbon to open the wizard.
3. Select your **Azure environment**, then select **Sign In**. Sign in to your account when prompted.
4. Ensure that **Use default settings (recommended)** is selected, then choose **Next** and **Yes** when the app registration notice appears.
5. Review the summary and select **Next** to cloud attach your environment and complete the wizard.

## Improvements to client health dashboard

This release includes improvements to the [Client health dashboard](../../clients/manage/client-health-dashboard).

[![An example of the updated Client Health Dashboard.](media/5728069-client-health-dashboard-small.png)](media/5728069-client-health-dashboard.png#lightbox)

- While you can configure the dashboard to limit the view by collection, previously it would reset to the **All Systems** collection when you refreshed the node. You can now select the ribbon action to **Choose Default Collection**, which sets a persistent user preference.
- You still use the **Client Status Settings** action to configure the periods of time to evaluate client health. This action is now available in the ribbon of the **Client health dashboard** node. This change makes it easier to access this action, without needing to switch to the parent node for **Client Status**.
- The existing options to filter the dashboard are now condensed to a single **Filter** tile.
- The **Overall client health** tile is on the top row, which makes it easier to see when you select this node. This percentage should be as close to 100% as possible.
- The **Combined (All)** and **Combined (Any)** scenarios are removed. A new tile, **Clients with any failure**, shows the percentage of clients that report any health issue. This percentage should be as close to 0% as possible.
- The dashboard includes a new tile for **Health trends by scenario**. It shows the percentage of healthy clients for the selected scenario. Use the slider control at the top of the tile to adjust the number of days to display in the chart.

    Note

    This maximum value for the slider control is the same as the **Retain client status history for the following number of days** in **Client Status Settings**. It's `31` days by default.

    It's limited by the amount of client health data in the site database. In the following example, while it's configured to display 31 days of history, there's only three days of available data.

    The following example shows the trend for client health evaluation:

    ![An example of the Client Health Dashboard, Health Trends By Scenario tile.](media/5728069-health-trends-hardware-inventory.png)

## Enable update notifications from Microsoft 365 Apps

You can now configure the end-user experience for Microsoft 365 Apps updates. This client setting allows you to enable or disable notifications from Microsoft 365 Apps for these updates. The new **Enable update notifications from Microsoft 365 Apps** option has been added to the **Software Updates** group of [client settings](../../clients/deploy/configure-client-settings). The following options are available for the setting:

- **No**: Doesn't display Microsoft 365 Apps updates notifications from Microsoft 365 Apps (default)
- **Yes**: Displays Microsoft 365 Apps updates notifications from Microsoft 365 Apps

### End-user experience for update notifications from Microsoft 365 Apps

Which notifications are displayed to the user about updates for Microsoft 365 Apps is also determined by the settings for per deployment notifications from Software Center. If deployment notifications from Software Center are disabled, then the end user won't receive any notifications from either Software Center or Microsoft 365 Apps, regardless of how notifications from Microsoft 365 Apps are set. If notifications from both Software Center and Microsoft 365 Apps are enabled, then the end user will receive notifications from Software Center and Microsoft 365 Apps. Below is a chart of which notifications for Microsoft 365 Apps updates are displayed to the end user for these settings:

| - | **Display**per deployment Software Center notifications | **Hide**per deployment Software Center notifications |
| --- | --- | --- |
| Enable update notifications from Microsoft 365 Apps: **Yes** | User receives notifications from Software Center  User receives notifications from Microsoft 365 Apps | No notifications from Software Center  No notifications from Microsoft 365 Apps |
| Enable update notifications from Microsoft 365 Apps: **No** | User receives notifications from Software Center  No notifications from Microsoft 365 Apps | No notifications from Software Center  No notifications from Microsoft 365 Apps |

## Branding in the Windows Update native reboot experience

You can now add branding information when using the native Windows restart experience for software updates. To use this feature, client devices must be running Windows Insider build 21277 or later. From the **Computer Restart** client device settings, ensure that **Windows** is selected as the restart experience. For the **Specify organization name** option, enter the organization name to display in the restart notifications. Branding information will be included in the Windows restart notification for updates that require restart.

![Screenshot of the computer restart notification for a client. The organization name is displayed in the notification and is outlined in red.](media/10543514-branded-restart.png)

## Improvements to application groups

This release includes the following improvements to [application group](../../../apps/deploy-use/create-app-groups):

- Now when you deploy an app group as required to a device or user collection, you can specify that it automatically uninstalls when the resource is removed from the collection. For more general information on this feature, see [Implicit uninstall](../../../apps/deploy-use/uninstall-applications#implicit-uninstall).
- The following [app approval](../../../apps/deploy-use/app-approval) behaviors are now supported with app groups:

    - Deploy an app group to a user collection and require approval.

        - A user can then request the app group in Software Center.
        - You can approve or deny the user's request for the app group.
    - Deploy an app group to a device collection and require approval. The deployment is suspended on the device until you trigger installation via automation. For example, use the [Approve-CMApprovalRequest](/en-us/powershell/module/configurationmanager/approve-cmapprovalrequest) PowerShell cmdlet.
    - From the Configuration Manager console, when you select a device, there's a new action in the **Device** group of the ribbon to **Install Application Group**. For more information, see [Install applications for a device](../../../apps/deploy-use/install-app-for-device).
    - When you enable tenant attach, you can view status and take actions on app groups from the Microsoft Intune admin center. For more information, see [Install an application from the admin center](../../../tenant-attach/applications).

### Known issues for app groups in this technical preview release

- If an app group was previously approved and installed on a device, the **Deny** action doesn't automatically uninstall it.
- To view and manage app groups in the Microsoft Intune admin center, your account needs the **Full Administrator** role in Configuration Manager.

## Improvements to external notifications

Starting in Configuration Manager current branch version 2107, you could enable the site to send notifications to an external system or application. This feature used a PowerShell script to manage the status filter rules and subscriptions. For more information, see [External notifications](../../servers/manage/external-notifications).

This release adds support in the Configuration Manager console to create or edit a subscription for external notifications. It supports events for status filter rules and application approval requests.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Create an Azure Logic App and copy the URL. For more information, see [Create an Azure logic app and workflow](../../servers/manage/external-notifications#create-an-azure-logic-app-and-workflow).
2. In the Configuration Manager console, go to the **Monitoring** workspace. Expand **Alerts**, and select the new **External service notifications** node.
3. In the ribbon, select **Create subscription**.
4. Specify a **Name** for the subscription to identify it in the Configuration Manager console. Optionally add a **Description**.
5. For the **External service URL** value, paste the URL of the Azure Logic App that you copied in the first step.
6. Select the gold asterisk ![](media/new-icon.png) to add a new event to the subscription.

How to trigger an event depends upon the type of subscription:

- For a status filter rule, trigger an event for the site component. For example, stop or restart the service or thread.
- For an app approval request, use Software Center to request an app that requires approval.

For more information on next steps, see [Monitor the workflow](../../servers/manage/external-notifications#monitor-the-workflow).

## Approvals for orchestration group scripts

Pre and post-scripts for [Orchestration groups](../../../sum/deploy-use/orchestration-groups) now require approval to take effect. If you open, author, or modify a script, approval for the script is required from another admin. When selecting an approved script from the [**Scripts** library](../../../apps/deploy-use/create-deploy-scripts), no additional approval is needed. By default, users can't approve a script they've authored. These roles give an additional level of security against running a script without oversight. For ease of testing, you're able to [disable script approval](../../../apps/deploy-use/create-deploy-scripts#allow-users-to-approve-their-own-scripts) for the environment by changing the hierarchy setting.

To assist you with script approval, the following two tabs were added to the details pane for **Orchestration Groups**:

- **Summary**: Contains information about the selected orchestration group, including the **Approval State** of scripts.
- **Scripts**: Lists information about pre and post-scripts, including the timeout, approver, and approval state for each script.

[![Screenshot of the Scripts tab for an orchestration group.](media/9957939-orchestration-group-scripts-tab.png)](media/9957939-orchestration-group-scripts-tab.png#lightbox)

### Approval states for pre and post-scripts

The approval state for each of the scripts is displayed in the **Scripts** tab. Editing a script after it's approved will reset the approval state. The **Approval State** for each script is defined below:

- **Approved**: The script is approved. Approval is granted from either of the following ways:
    - Selecting a script from the list of approved PowerShell scripts
    - Manual approval of the script by selecting **Approve** from the ribbon or the right-click menu.
- **Waiting for approval**: The script is pending approval. Scripts that are written or edited directly in the code editor, or imported from a `.ps1` file will start in this approval state.
- **Declined**: The script was denied during the approval process.

Important

Editing a script after it's approved will reset the approval state to **Waiting for approval**. This also means that the previously approved version of the script will not run if you start orchestration on the group while that script is in the **Waiting for approval** state.

### Permissions

Approving scripts for orchestration groups requires one of the following security roles:

- Full Administrator
- Operations Administrator

### Approve or deny a script for an orchestration group

1. From the Configuration Manager console, go to the **Assets and Compliance** workspace &gt; **Overview** &gt; **Orchestration Groups**.
2. Select an orchestration group and then select the **Scripts tab** for the group.
3. Select one of the scripts and choose **Approve/Deny** from either the ribbon or the right-click menu.
4. Review the script from the **Script Details** page in the **Approve or Deny Script** wizard. Select **Next** when you're finished reviewing the script.
5. On the **Script Approval** page in the wizard, select **Approve** or **Deny**. If needed, enter in a comment to be displayed in the **Scripts** detail pane.
6. Complete the wizard to finish the approval process.

## Task sequence check for TPM 2.0

To help you better deploy Windows 11, the [Check Readiness](../../../osd/understand/task-sequence-steps#BKMK_CheckReadiness) step in the task sequence now includes checks for TPM 2.0.

- **TPM 2.0 or above is enabled**: Checks whether the device that's running the task sequence has a TPM 2.0 that's enabled.
- **TPM 2.0 or above is activated**: If the device has an enabled TPM 2.0, check that it's activated.

The task sequence smsts.log file also shows the TPM version.

## Console improvements

Based on your feedback, this release includes the following improvements to the Configuration Manager console:

- When you show the members of a device collection, and select a device in the list, switch to the **Collections** tab in the details pane. This new view shows the list of collections of which the selected device is a member. It makes it easier for you to see this information.

    ![Collections tab in the details pane of the list of collection members.](media/10480635-collections-tab.png)
- When viewing a collection, you could previously see the amount of time the site took to evaluate the collection membership. This data is now also available in the **Monitoring** workspace. When you select a collection in either subnode of the **Collection Evaluation** node, the details pane displays this collection evaluation time data.

    ![Full Evaluation Status node in the Monitoring workspace of the Configuration Manager console, showing collection evaluation times.](media/9648622-collection-evaluation-data.png)

## Status messages for console extensions

To improve the visibility and transparency of [console extensions](../../servers/manage/admin-console-extensions), the site now creates status messages for related events. These status messages have IDs from **54201** to **54208**. They all include the following information:

- The user that made the change
- The ID of the extension
- The version of the extension

There are four categories of message events:

- Required or optional
- Approve or disapprove
- Enable or disable
- Tombstone or untombstone

For example, the description of status message ID **54201** is **User `"%1"` made console extension with ID `"%2"` and version `"%3"` required**.

Use these status messages to make sure your site uses known and trusted console extensions.

## General known issues

### Community hub download button is always enabled

The **Download** button for items in **Community hub** doesn't disable once an object has been downloaded. The download will fail if you attempt to download the item again.