---
layout: Conceptual
title: Technical preview 2011 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2011
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2011.
ms.date: 2020-11-25T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: eaec672e-5e42-3f34-7ab1-ab7edc829240
document_version_independent_id: f11cfdc7-b456-aa9e-4bcc-fcc11536499d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2011.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2011
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2011.md
platformId: 2c79ccb6-7d30-1bc5-221a-0b00af758738
---

# Technical preview 2011 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2011. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Categorize Community hub content

Community hub content is grouped into a Microsoft, curated, or unreviewed category to allow admins to choose the types of content their environment displays. Admins can choose from the different categories of content that are provided in the [Community hub](../../servers/manage/community-hub) to match their risk profile and their willingness to share and use content from those outside Microsoft and outside their own company.

Community hub content has three categories for content sources:

- **Microsoft curated**: Content provided by Microsoft
- **Community curated**: Content provided by the community that gets reviewed by Microsoft
- **Community unreviewed**: General content from the community that doesn't get reviewed by Microsoft

![The three categories for content sources for Community hub](../media/8052494-community-hub-content-sources.png)

Admins can choose the types of content their environment displays from the following options:

- **Display Microsoft content**: Selecting this option means that only content created by Microsoft will be shown in the Community hub. This content has had some basic testing and scanning validation to confirm no malware and inappropriate text.
- **Display Microsoft and curated community content**: Show curated content from both Microsoft and community partners with basic level of review. Selecting this option means that only content that has been curated will be shown. The curation process includes basic review to confirm that the content doesn’t have malware and inappropriate text, but hasn’t necessarily been tested. It will include content from the community, not just from Microsoft.
- **Display all content including unreviewed content**: Selecting this option means that all content is shown. This option includes unreviewed open-source type samples from the community, meaning that the content hasn’t necessarily been reviewed at all. It's provided as-is as open-source type sample content. Doing your own inspection and testing before using is highly encouraged, which is good practice on any content, but especially this class of content.

![Hierarchy settings for allowed content sources for Community hub](../media/8052494-community-hub-content-hierarchy-settings.png)

Since the content is *open-source* style content, admins should always review what is provided before consuming it. The new curation process is intended to vet the material to make sure there aren't obvious quality or compliance issues, but it will be somewhat of a cursory review. All content stored within GitHub and accessed from the Community hub isn’t supported by Microsoft. Microsoft doesn’t validate content collected from or shared by the general community. For more information, see [GitHub Terms of Service](https://help.github.com/terms) and [GitHub Privacy Statement](https://help.github.com/privacy).

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Permissions

Full Administrators can opt in the hierarchy for unreviewed content via hierarchy settings. Lower hierarchy administrators can't opt in the hierarchy for unreviewed hub items.

Most [built-in security roles](../../understand/fundamentals-of-role-based-administration) will have access to Community hub:

| Role name | View the hub | Contribute hub content | Download hub content |
| --- | --- | --- | --- |
| Remote Tools Operator | No | N/A | N/A |
| Read Only Analyst | Yes | No | No |
| All other roles | Yes | Yes | Yes |

#### Select the content categories to display in Community hub for the environment

1. In the Configuration Manager console, go to **Administration** &gt; **Overview** &gt; **Site Configuration** &gt; **Sites**.
2. Select the top-level site in your hierarchy and select **Hierarchy Settings** from the ribbon.
3. On the **General** tab, change the **Community hub** setting to **Display Microsoft content**.
4. Select **Ok** when you're finished changing the hierarchy setting.
5. Open the **Community hub** node in the **Community** workspace.
6. Ensure that only Microsoft content is displayed and available for download.
7. Go back to **Hierarchy Settings** and select another option such as **Display all content, including unreviewed content**.
8. Confirm that only the type of content is displayed and able to be downloaded from the Community hub, that matches the corresponding hierarchy setting category.

## Improvements to the product lifecycle dashboard

This release includes improvements to the [product lifecycle dashboard](../../clients/manage/asset-intelligence/product-lifecycle-dashboard) to make it more actionable for you.

- Customize the timeframe on the charts for your preference.
- Search, sort, and filter the data.
- View a list of devices with products that are near or at end of support, and you need to update.

The dashboard also has a new subnode, **All Product Lifecycle Data**. You can sort and filter the product lifecycle information, which gives you multiple ways to view it. When you select a product, you can **View devices** for that product. From the list of devices, you can currently create a direct membership collection. Use this action to deploy the latest software versions to these collections so that the devices are kept current.

The dashboard has a new time slider. Use it to control the timeframe for the **Top 5 products nearing end-of-support** tile. The default is 18 months, but you can adjust it from 1 to 36 months.

![Product lifecycle dashboard highlighting new timescale control at 33 months](media/8160460-product-lifecycle-timescale.png)

## Software Center notifications display with logo

If you enable Software Center customizations, then notifications on Windows 10 devices display the logo that you configure in client settings. This change helps users to trust these notifications.

When you deploy software to a client, the user sees notifications with your logo. The following example uses a star logo:

![New software is available notification with custom logo](media/4993167-notification-with-logo.png)

For more information about customizing Software Center, see [About client settings: Software Center](../../clients/deploy/about-client-settings#software-center).

## Approved scripts for Orchestration Groups

You can now select from scripts that were approved when configuring pre and post-scripts for an [orchestration group](../../../sum/deploy-use/orchestration-groups). When in the **Create Orchestration Group Wizard**, you'll see a new page called **Script Picker**. Select your pre and post scripts from your list of scripts that are already approved. You can still add scripts manually on the pre and post-script pages. Additionally, you can also edit scripts that you prepopulated from the **Script Picker**.

[![Script Picker page in the Create Orchestration Group Wizard](../media/6991647-approved-scripts-orchestration-group.png)](../media/6991647-approved-scripts-orchestration-group.png#lightbox)

## Community hub on Windows Server operating systems

You can now display the Community hub on Windows Server operating systems. Follow the instructions below to enable Windows Server 2012 and later to load the Community hub:

1. In the upper-right corner of the console, select the bell icon to display Configuration Manager console notifications.

    ![Notifications in the Configuration Manager console](../media/3555909-notification.png)
2. The notification will say **New custom console extensions are available**.

    ![New custom console extensions are available notification](../media/3555909-extension-notification.png)
3. Select the link **Install custom console extensions** to launch the install.
4. When the install completes, select **Close** to restart the console.

    ![Console extension completed install](../media/3555909-extension-installed.png)
5. Confirm that you can view the **Community hub** node from the machine running the Windows Server operating system.

    - You may also notice that a new folder `AdminConsole\bin\Microsoft.WebView2.FixedVersionRuntime.<version>.x86` was created.
    - The files are automatically downloaded from https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section with the other redistributable files.

## Improvements to Support Center

When you troubleshoot software update deployments, you might ask the following questions:

- Are any updates missing or failing?
- Are specific updates deployed to a device?
- What are the error codes for a deployment?
- Why didn't the device reboot during a maintenance window?
- What's the current state of an update?

Support Center already shows updates that are targeted to the device but not yet installed. Now in this release, select **All Updates** on the **Content** tab of Support Center to show all updates targeted to the device. To help you troubleshoot, this list includes information about whether the update is installed or missing.

Also on the **Content** tab, select **Maintenance Windows** to show the available maintenance windows for the device.

For more information on the additional features of Support Center that you can use to help troubleshoot a device, see [Support Center overview](../../support/support-center).

## Improvements to OS deployment

This release includes the following improvements to OS deployment:

- Based on your feedback, task sequence conditions now include a **not like** operator. This operator applies to task sequence variable conditions. It's also used in the [Set Dynamic Variable](../../../osd/understand/task-sequence-steps#BKMK_SetDynamicVariables) task sequence step.
- Based on your feedback, this release fixes issues with the [SMSTSDisableStatusRetry](../../../osd/understand/task-sequence-variables#SMSTSDisableStatusRetry) task sequence variable.
- Based on your feedback, the [Check Readiness](../../../osd/understand/task-sequence-steps#BKMK_CheckReadiness) task sequence step now also checks free space on disks without partitions.
- Based on your feedback, the following PowerShell cmdlets now have an **Index** parameter:

    - [New-CMOperatingSystemImage](/en-us/powershell/module/configurationmanager/new-cmoperatingsystemimage): When you run this cmdlet with the new **Index** parameter, it creates a new single-index image file in the same source folder.
    - [New-CMOperatingSystemInstaller](/en-us/powershell/module/configurationmanager/new-cmoperatingsysteminstaller) (alias **New-CMOperatingSystemUpgradePackage**): When you run this cmdlet with the new **Index** parameter, it replaces the original image file in the source folder with a single-index image file.
- Based on your feedback, the following new cmdlets are available to get the list of existing hardware IDs in the site database:

    - **Get-CMDuplicateHardwareIdGuid**
    - **Get-CMDuplicateHardwareIdMacAddress**

    These new cmdlets supplement the existing cmdlets to add and remove duplicate IDs. For more information, see [Version 1910 PowerShell release notes](/en-us/powershell/sccm/1910-release-notes#new-cmdlets).

## Update PowerShell help

You can now use the [Update-Help](/en-us/powershell/module/microsoft.powershell.core/update-help) cmdlet to get the latest information for the Configuration Manager PowerShell module. This content is the same as what's published for the [ConfigurationManager module](/en-us/powershell/module/configurationmanager/).

The computer on which you run this cmdlet needs internet access, specifically `pshelpprod.blob.core.windows.net`. Then run the following command:

```powershell
Update-Help –Module ConfigurationManager
```

Then use the **Get-Help** cmdlet, for example:

```powershell
Get-Help Get-CMDevice
Get-Help Get-CMDevice -Examples
Get-Help Get-CMDevice -Parameter *
```

For more information, see the following PowerShell blog post: [You’ve got Help!](https://devblogs.microsoft.com/powershell/youve-got-help/).