---
layout: Conceptual
title: Technical preview 2010 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2010
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2010.
ms.date: 2020-10-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 2291d770-bbac-6ad0-7ead-470adb230507
document_version_independent_id: 12648e05-1b6b-d720-95f5-4fb5142b106c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2010.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2010
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2010.md
platformId: 02e78a2e-8ef0-d050-40dc-c6d96b617859
---

# Technical preview 2010 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2010. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Desktop Analytics support for Windows 10 Enterprise LTSC

The Windows 10 long-term servicing channel (LTSC) was designed for devices where the key requirement is that functionality and features don't change over time. This servicing model prevents Windows 10 Enterprise LTSC devices from receiving the usual feature updates. It provides only quality updates to make sure that device security stays up to date. Some customers want to shift from LTSC to the semi-annual servicing channel, to have access to new features, services, and other major changes. Starting in this release, you can now enroll LTSC devices to Desktop Analytics to evaluate in your deployment plans.

## Improvements to scenario health

Technical preview version 2008 added the ability to [monitor scenario health](technical-preview-2008#bkmk_health), which initially focused on SQL Server Service Broker. In this release, you can now monitor the health of the fast channel used for client actions. If your environment is [tenant attached with devices uploaded](../../../tenant-attach/device-sync-actions), this feature helps you see potential issues with client actions from the Microsoft Intune admin center. You can also use this feature for on-premises client actions. For example, CMPivot, run scripts, and device wake-up.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Monitoring** workspace, and select the **Scenario Health** node. The list view displays the available scenarios.
2. Select the **Client action health** scenario, then in the ribbon, select **Show Status**. This action opens a window with more information. The top section shows the overall status per site. Select a site, to see more detailed status for that site in the bottom section.

    ![Client action health example output](../media/7699511-client-action-health.png)

## Expanded Windows Defender Application Control management

[Windows Defender Application Control](../../../protect/deploy-use/use-device-guard-with-configuration-manager) enforces an explicit list of software allowed to run on devices. In this technical preview, we've expanded Windows Defender Application Control policies to support devices running Windows Server 2019 or later. 

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Configure a new Windows Defender Application Control policy

1. In the Configuration Manager console, go to **Assets and Compliance** &gt; **Overview** &gt; **Endpoint Protection** &gt; **Windows Defender Application Control**.
2. In the ribbon, select **Create Application Control Policy**.
3. Give your policy a **Name**, an optional **Description**, and select your **Enforcement Mode**.
4. Specify any additional files and folders to be included as trusted software on the **Inclusions** page of the wizard. Select **Next** when you're finished.
5. On the **Summary** page, select **Next** after reviewing your settings, then **Close** to complete the wizard.

#### Deploy the policy to a collection containing devices running Windows Server 2019 or later

1. In the **Windows Defender Application Control**, select the new policy you created.
2. Select **Deploy Application Control Policy** from the ribbon.
3. Use the **Browse** button to choose a collection containing devices running Windows Server 2019 or later.
4. If needed, specify the following options:
    - A custom compliance evaluation schedule for the application control policy
    - Allowing remediation outside a maintenance window
5. Select **OK** to deploy the policy.

Tip

Create new policies to target Windows Server operating systems. Existing Windows Defender Application Control policies won't work with Windows Server operating systems.

## Syntax highlighting for scripting languages

To assist you when creating scripts and queries in the Configuration Manager console, you'll now see syntax highlighting and code folding, where available.

[![Syntax highlighting in console](media/7964912-syntax-highlighting.png)](media/7964912-syntax-highlighting.png#lightbox)

### Supported scripting languages for syntax highlighting

Supported languages for syntax highlighting include PowerShell, JavaScript/JScript, VBScript, and SQL/WQL. The below chart shows which languages are supported for syntax highlighting in each area of the console:

| Console area | PowerShell | VBScript | JavaScript/JScript | SQL/WQL |
| --- | --- | --- | --- | --- |
| Application scripts | Yes | Yes | Yes | - |
| Collection query | - | - | - | Yes |
| Configuration item scripts | Yes | Yes | Yes | Yes |
| Task sequence scripts | Yes | - | - | - |
| Create scripts | Yes | - | - | - |

## Deploy a task sequence to a user

Based on your feedback, you can now deploy a non-OS deployment task sequence to a user-based collection. Use the task sequence deployment type of an application to install or uninstall it.

For more information, including the list of prerequisites, see [Task sequence deployment type](../../../apps/get-started/creating-windows-applications#bkmk_tsdt).

Note

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Shortcuts to status messages

Based on your feedback, you now have an easier way to view status messages for the following objects:

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

## Enable user proxy for software update scans

Beginning with the September 2020 cumulative update, HTTP-based WSUS servers will be secure by default. A client scanning for updates against an HTTP-based WSUS will no longer be allowed to leverage a user proxy by default. If you still require a user proxy despite the security trade-offs, a new [software updates client setting](../../clients/deploy/about-client-settings#software-updates) is available to allow these connections. For more information, see [September 2020 changes to improve security for Windows devices scanning WSUS](https://go.microsoft.com/fwlink/?linkid=2144403).

To enable a user proxy for software update scans:

1. In the Configuration Manager console, choose **Administration** &gt; **Client Settings**.
2. Select either the **Default Client Settings** or the set of custom client device settings to edit.
3. On the **Home** tab, choose **Properties**.
4. Select the **Software Updates** group of settings.
5. Set **Allow user proxy for software update scans** to **Yes**.

When the client policy refreshes, devices will get the new value and apply it during the next scan cycle.

## Improvements to task sequence performance for power plans

Starting in Configuration Manager version 1910, to improve the overall speed of the task sequence, you can activate the Windows power plan for **High Performance**. Starting in this technical preview release, you can now use this option on devices with [modern standby](/en-us/windows-hardware/design/device-experiences/modern-standby) and other devices that don't have that default power plan. Now when you use this task sequence option, it creates a temporary power plan that's similar to the default for **High Performance**. After the task sequence completes, it reverts to the original power plan, and deletes the temporary plan.

For more information on this option, see [Task sequence performance](../../../osd/deploy-use/task-sequence-performance).