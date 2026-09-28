---
layout: Conceptual
title: Technical Preview 1707 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1707
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
description: Learn about features available in the Technical Preview version 1707 for Configuration Manager.
ms.date: 2017-08-14T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 2989f358-5b90-9755-957c-e3a2a4ef6a60
document_version_independent_id: 1e6d2d1f-de47-dc25-17ab-8c8c8f088dc7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1707.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1707
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1707.md
platformId: 26086505-5b8f-52e9-7b58-caefd69ba361
---

# Technical Preview 1707 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the Technical Preview for Configuration Manager, version 1707. You can install this version to update and add new capabilities to your Configuration Manager technical preview site. Before installing this version of the technical preview, review [Technical Preview for Configuration Manager](technical-preview) to become familiar with general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback about the features in a technical preview.

**Known Issues in this Technical Preview:**

- **Update to preview version 1707 fails when you have a site server in passive mode**. When you run the preview version 1706 and have a [primary site server in passive mode](capabilities-in-technical-preview-1706#site-server-role-high-availability), you must uninstall the passive mode site server before you can successfully update your preview site to version 1707. You can reinstall the passive mode site server after your site runs version 1707.

    To uninstall the passive mode site server:

    1. In the console go to **Administration** &gt; **Overview** &gt; **Site Configuration** &gt; **Servers and Site System Roles**, and then select the passive mode site server.
    2. In the **Site System Roles** pane, right click on the **Site server** role, and then choose **Remove Role**.
    3. Right-click on the passive mode site server, and then choose **Delete**.
    4. After the site server uninstalls, on the active primary site server restart the service **CONFIGURATION\_MANAGER\_UPDATE**.

**The following are new features you can try out with this version.**

## Client Peer Cache support for express installation files for Windows 10 and Microsoft 365

Beginning with this release, Peer Cache supports distribution of content express installation files for Windows 10, and of update files for Microsoft 365. No additional configurations are required.

## Surface Device dashboard

The Surface Device dashboard provides information about the Surface devices found in your environment. In the console, go to **Monitoring** &gt; **Surface Devices**. You can view the following:

- percent of Surfaces
- percent of Surface models
- top five operating system versions

Click a section of the **Surface Models** chart for a complete list of the devices.

## Configure and deploy Windows Defender Application Guard policies

[Windows Defender Application Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) is a new Windows feature that helps protect your users by opening untrusted web sites in a secure isolated container that is not accessible by other parts of the operating system. In this technical preview, we've added support to configure this feature using Configuration Manager compliance settings which you configure, and then deploy to a collection. This feature will be released in preview for the 64-bit version of the Windows 10 Fall Creator's Update (code name: RS3). To test this feature now, you must be using a preview version of this update.

### Before you start

To create and deploy Windows Defender Application Guard policies, the Windows 10 devices to which you deploy the policy must be configured with a network isolation policy. For more details, see [this blog post](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). This capability works only with current Windows 10 Insider builds. To test it, your clients must be running a recent Windows 10 Insider Build.

### Try it out!

#### To create a policy, and to browse the available settings:

1. In the Configuration Manager console, choose **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, choose **Overview** &gt; **Endpoint Protection** &gt; **Windows Defender Application Guard**.
3. In the **Home** tab, in the **Create** group, click **Create Windows Defender Application Guard Policy**.
4. Using the blog post as a reference, you can browse and configure the available settings to try the feature out.
5. In this release, we've added the new **Network Definition** page to the wizard. On this page, specify the corporate identity, and define your corporate network boundary.Windows 10 PCs store only one network isolation list on the client. In this release, you can create two different kinds of network isolation lists (one from Windows Information Protection, and one from Windows Defender Application Guard), and deploy them to the client. If you deploy both policies, these network isolation lists must match. If you deploy lists that don't match to the same client, the deployment will fail. You can find more information about how to specify network definitions in the [Windows Information Protection documentation](/en-us/windows/security/information-protection/windows-information-protection/create-wip-policy-using-configmgr).
6. When you are finished, complete the wizard, and deploy the policy to one or more Windows 10 devices.

### Further reading

To read more about Windows Defender Application Guard, see [this blog post](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Additionally, to learn more about Windows Defender Application Guard Standalone mode, see [this blog post](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).

## Add parameters when you deploy PowerShell scripts from Configuration Manager

In the last Technical Preview, we introduced a new capability that lets you [Create and run PowerShell scripts from the Configuration Manager console](capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console). In this Technical Preview, we've expanded on this capability. Configuration Manager now reads the PowerShell script, and displays any parameters in the Create Script Wizard. You can supply a value for the parameter in the wizard that will be used when the script is run. Alternatively, you can leave the parameter blank. If you do this, you will need to supply a value for the parameter when you run the script. In this technical preview, you must supply any parameters that a script requires. In a future release, we plan to make supplying script parameters optional.

### Try it out!

1. Follow the instructions to [Create and run PowerShell scripts from the Configuration Manager console](capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console).
2. On the new **Script Parameters** page of the **Create Script Wizard**, choose a parameter, and then click **Edit**.
3. Supply a parameter value for the selected parameter, and then click **OK**.
4. Complete the wizard.

When the script runs, it will use any parameter values you configured.