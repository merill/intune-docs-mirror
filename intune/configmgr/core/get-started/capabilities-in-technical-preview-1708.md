---
layout: Conceptual
title: Technical Preview 1708 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1708
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
description: Learn about features available in the Technical Preview version 1708 for Configuration Manager.
ms.date: 2017-08-25T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: c9d2bda6-c98c-2839-6bc7-7a5108a830aa
document_version_independent_id: 3916389e-52f4-d631-247b-cdd3c4979ff0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1708.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1708
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1708.md
platformId: 89102470-327b-c597-2097-93dafa420807
---

# Technical Preview 1708 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the Technical Preview for Configuration Manager, version 1708. You can install this version to update and add new capabilities to your Configuration Manager technical preview site. Before installing this version of the technical preview, review [Technical Preview for Configuration Manager](technical-preview) to become familiar with general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback about the features in a technical preview.

**Known Issues in this Technical Preview:**

- **Update to preview version 1708 fails when you have a site server in passive mode**. When you run the preview version 1706 or 1707, and have a [primary site server in passive mode](capabilities-in-technical-preview-1706#site-server-role-high-availability), you must uninstall the passive mode site server before you can successfully update your preview site to version 1708. You can reinstall the passive mode site server after your site runs version 1708.

    To uninstall the passive mode site server:

    1. In the console go to **Administration** &gt; **Overview** &gt; **Site Configuration** &gt; **Servers and Site System Roles**, and then select the passive mode site server.
    2. In the **Site System Roles** pane, right click on the **Site server** role, and then choose **Remove Role**.
    3. Right-click on the passive mode site server, and then choose **Delete**.
    4. After the site server uninstalls, on the active primary site server restart the service **CONFIGURATION\_MANAGER\_UPDATE**.

**The following are new features you can try out with this version.**

## Improvements for specifying script parameters when you deploy PowerShell scripts from Configuration Manager

From Configuration Manager 1706 onwards, you can [Create and run PowerShell scripts from the Configuration Manager console](../../apps/deploy-use/create-deploy-scripts).

In [Technical Preview 1707](capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager), we expanded on this capability to let Configuration Manager read parameters from the script.

In this Technical Preview, we've expanded the script parameters capability to detect which parameters are mandatory, and which are optional, and prompt you to enter these.

### Try it out!

1. Follow the instructions to [Create and run PowerShell scripts from the Configuration Manager console](../../apps/deploy-use/create-deploy-scripts).
2. On the new **Script Parameters** page of the **Create Script Wizard**, choose a parameter, and then edit its values. The wizard displays which parameters are mandatory, and which are optional.
3. When you have finished editing parameters, complete the wizard.

When the script runs, it will use any parameter values you configured. If you did not configure a mandatory parameter, the end user will be asked to supply the parameter when the script runs.

## Management insights

You can now gain insights into the current state of your environment based on analysis of data in the site database. Insights help you to better understand your environment and take action based on the insight. Review management insights in the Configuration Manager console at **Administration** &gt; **Management Insights** &gt; **All Insights**. In this release, the following insights are now available:

- **Applications without deployments**: Lists the applications in your environment that do not have active deployments. This helps you to find and delete unused applications to simplify the list of applications displayed in the console.
- **Empty collections**: Lists the collections in your environment that have no members. You can delete these collections to simplify the list of collections displayed when deploying objects, for example.

## Restart computers from the Configuration Manager console

Beginning with this release, you can use the Configuration Manager console to identify client devices that require a restart, and then use a client notification action to restart them.

To identify devices that are pending a restart, go to **Assets and Compliance** &gt; **Devices** and select a collection with devices that might need a restart. After you select a collection you can view the status for each device in the details pane in a new column named **Pending Reboot**. Each device has a value of **Yes**, or **No**.

To create the client notification to restart a device:

1. Locate the device you want to restart in the Devices node of the console.
2. Right-click on the device, select **Client Notification**, and then select **Reboot**. This opens an information window about the restart. Click **OK** to confirm the restart request.

When the notification is received by a client, a **Software Center** notification window opens to inform the user about the restart. By default, the restart occurs after 90 minutes. You can modify the restart time by configuring [client settings](../clients/deploy/configure-client-settings). Settings for the restart behavior are found on the [Computer restart](../clients/deploy/about-client-settings#computer-restart) tab of the default settings.

### Try it out!

Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:

1. Deploy an app or update to a device that will require that device to restart to complete installation.
2. Locate the device in the **Assets and Compliance** &gt; **Devices** node of the console and confirm it displays **Yes** in the **Pending Reboot** column. It can take up to 20 minutes for the Pending Reboot status to be reflected in the console.
3. Monitor the device to confirm that the Software Center notification opens, and that the device successfully restarts.

## Software Center customization

You can add enterprise branding elements and specify the visibility of tabs on Software Center. You can add your Software Center specific company name, set a Software Center configuration color theme, set a company logo, and set the visible tabs for client devices.

### Customize Software Center

To modify Software Center:

1. In the **Configuration Manager** console, choose **Administration** &gt; **Client Settings**. Click on your desired client setting instance.
2. On the **Home** tab, in the **Properties** group, choose **Properties**.
3. In the **Default Settings** dialog box, choose **Software Center**.
4. Select **Yes** to **Select new settings to specify company information** to enable your Software Center customization settings.
5. Type your **Company name**.
6. Select your **Color Scheme for Software Center**.
7. Click **Browse** to navigate to your logo for Software Center. The logo must be a JPEG or PNG of 400 x 100 pixels with a maximum size of 750 KB.
8. Select **YES** to make tabs visible in the Software Center for client devices. At least one tab must be visible:

    - Enable Applications tab
    - Enable Updates tab
    - Enable Operating Systems tab
    - Enable Installation Status tab
    - Enable Device compliance tab
    - Enable Options tab

### Next steps

To learn more about application management in Configuration Manager, see [Introduction to application management](/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management).