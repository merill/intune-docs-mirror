---
layout: Conceptual
title: Technical preview 1908 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1908
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1908.
ms.date: 2019-08-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 0cec8bab-33dc-a437-229f-72c47775649a
document_version_independent_id: 6f7603ad-07a5-1d4b-69fa-507078c8413b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1908.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1908
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1908.md
platformId: dac45499-f7e2-3044-63c9-8bd2c8725e90
---

# Technical preview 1908 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1908. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Task sequence performance improvements for power plans

Based on your feedback, you can now run a task sequence with the high performance power plan. This option improves the overall speed of the task sequence. It configures Windows to use its built-in high performance power plan, which delivers maximum performance at the expense of higher power consumption.

When the task sequence starts, it records the currently enabled power plan. It then switches the active power plan to the Windows default **High Performance** plan. If the task sequence restarts the computer, it repeats this process. At the end of the task sequence, it resets the power plan to the stored value. This functionality works in both Windows and Windows PE, but has no impact on virtual machines.

Important

To take advantage of this new Configuration Manager feature, after you update the site, update clients to the latest version. Also update boot images to include the latest client components. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Operating Systems**, and select the **Task Sequences** node.
2. Create or choose an existing task sequence, and then select **Properties**.
3. Switch to the **Performance** tab.
4. Enable the option to **Run as high performance power plan**.

Warning

Be cautious with this setting on low performance hardware. Running intense system operations for an extended period of time can strain low-end hardware. Check with your hardware manufacturer for specific guidance.

## Local device query evaluation using CMPivot standalone

When using CMPivot outside of the Configuration Manager console, you can query just the local device without the need for the Configuration Manager infrastructure. You can now use the CMPivot Azure Log Analytics queries to quickly view WMI information on the local device. This tool also enables validation and refinement of CMPivot queries, before running them in a larger environment. CMPivot standalone is a [pre-release feature](../../servers/manage/pre-release-features#list-of-pre-release-features) and is only available in English. For more information about installing CMPivot standalone, see [Install CMPivot standalone](../../servers/manage/cmpivot#install-cmpivot-standalone).

## Additional software update filter for ADRs

As a result of your feedback, now you can use **Deployed** as an update filter for your automatic deployment rules. This filter helps identify new updates that may need to be deployed to your pilot or test collections. The software update filter can also help avoid redeploying older updates. When using **Deployed** as a filter, be mindful that you may have already deployed the update to another collection, such as a pilot or test collection.

![Add IsDeployed as an update filter to an automatic deployment rule](media/4852033-isdeployed-adr-filter.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

To create a new ADR:

1. Go to **Software Library** &gt; **Software Updates** &gt; **Automatic Deployment Rules**.
2. In the ribbon, click **Create Automatic Deployment Rule**.
3. Specify your settings on the **General** and **Deployment Settings** pages in the wizard.
4. When you get to the **Software Updates** page, select **Deployed** and choose either **Yes** or **No**.
5. Complete the rest of your ADR selections by following the rest of the wizard.

Change an existing ADR:

1. Go to **Software Library** &gt; **Software Updates** &gt; **Automatic Deployment Rules**.
2. Right-click on the automatic deployment rule you want to modify and select **Properties**.
3. In the **Software Updates** tab, select **Deployed** and choose either **Yes** or **No**.
4. Click **OK** to save and close the properties page. The new filter will be used the next time the rule is run.

## Use Delivery Optimization for all Windows updates

Previously, Delivery Optimization could be leveraged only for express updates. With this technical preview, it's now possible to use Delivery Optimization for the distribution of all Windows Update content for clients running Windows 10 version 1709 or later.

### Prerequisites

Enable the following [software updates client settings](../../clients/deploy/about-client-settings#software-updates):

- **Allow clients to download delta content when available** set to **Yes**
- **Port that clients use to receive requests for delta content** set to 8005 (default) or a custom port number

Delivery Optimization must be enabled (default) and not bypassed. For more information, see [Windows Delivery Optimization](../../../sum/deploy-use/optimize-windows-10-update-delivery#windows-delivery-optimization).

### Log files

For clients running Windows 10 version 1709 or later, use the following log files to monitor delta downloads:

- WUAHandler.log
- DeltaDownload.log

## Phased deployment templates

In the same way that it's possible to create deployment templates, it's now possible to create and use phased deployment templates for software updates. Templates will save you time when configuring other phased deployments with similar settings.

![Use a template for phased deployments](media/4961086-phased-deployment-use-template.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

Create a phased deployment template:

1. In the ribbon, select **Create Phased Deployment** for one of the following objects:

    - Task sequence
    - Software update or software update group
    - Application
2. Specify your usual settings for your phased deployment.
3. When you get to the **Summary** page, click the **Save As Template...** option.
4. Give your template a name and select which settings to save in your template.
5. Click **Save**. Use your new template the next time you create a phased deployment.

![Save a template for phased deployments](media/4961086-phased-deployment-save-template.png)

## Improvements to console connections node

In the **Console Connections** node, The **Last Console Heartbeat** column has replaced **Last Connected Time**. The **Last Console Heartbeat** column gives administrators more information for determining which console connections are currently active. When a Configuration Manager console is open, a check is made every 10 minutes. If the console is running in the foreground during the check, the **Last Console Heartbeat** column is updated.

## Copy and paste task sequence conditions

If you want to reuse the conditions from one task sequence step to another, based on your feedback, you can now copy and paste conditions in the task sequence editor. Select a condition to cut or copy it. If a condition has children, it copies the entire block. If there's a condition on the clipboard, you can paste it with the following options:

- Paste before
- Paste after
- Paste under (only applies to nested conditions)

Use standard keyboard shortcuts to copy (**CTRL** + **C**) and cut (**CTRL** + **X**). The standard **CTRL** + **V** keyboard shortcut does the **Paste after** action.

There are also new options to move conditions up or down the list.

![New controls on Options tab of task sequence editor](media/4621098-copy-paste-ts-condition.png)

Note

You can copy and paste conditions between steps in a task sequence. It doesn't support this action between different task sequences.

## Improvements to task sequence editor search

This release includes the following improvements to the version 1907 feature to [search the task sequence editor](technical-preview-1907#bkmk_tsedit):

- The list of search options is now named **Scope**. Use it to choose the areas of the task sequence editor to search. You can now use **Alt** + **Down arrow** to open this list.
- Instead of scoping the search to the **Group**, you can now search on **Group Name** or **Group Description**.

![Improvements to searching the task sequence editor](media/4621085-task-sequence-search-1908.png)

## Improvements to OS deployment

This release includes the following improvements to OS deployment:

- Based on your feedback, configure the default keyboard layout for a boot image. On the **Customization** tab of a boot image, use the new option to **Set default keyboard layout in WinPE**. In the console, if you select a language other than en-us, Configuration Manager still includes en-us in the available input locales. On the device, the initial keyboard layout is the selected locale, but the user can switch the device to en-us if needed.

    Tip

    The [Set-CMBootImage](/en-us/powershell/module/configurationmanager/set-cmbootimage) PowerShell cmdlet now includes a new parameter, `-InputLocale`. For example:

    ```PowerShell
    # Set boot image keyboard layout to Russian (Russia)
    Set-CMBootimage -Id "CM100004" -InputLocale "ru-ru"`
    ```
- Based on your feedback, the **Run Command Line** step now includes an option to **Output to task sequence variable**. When you enable this option, the task sequence saves the output from the command to a custom task sequence variable that you specify.

    Note

    Configuration Manager now limits this output to the last 1000 characters. This change applies to both the **Run Command Line** and **Run Powershell Script**. For more information, see [About task sequence steps](../../../osd/understand/task-sequence-steps) steps.
- When importing an OS upgrade package, you can **Extract a specific image index from install.wim file of selected upgrade package**. This behavior is similar as with [OS images](../../../osd/get-started/manage-operating-system-images#BKMK_AddOSImages), except it overwrites the existing install.wim in the OS upgrade package. It extracts the image index to a temporary location, and then moves it into the original source directory.

    Warning

    Before you import an OS upgrade package and enable this option, make sure to backup the original source files. Configuration Manager overwrites the install.wim in the source to use the extracted image index.
- Based on your feedback, use the following PowerShell cmdlets to automate the management of [duplicate hardware identifiers](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network#manage-duplicate-hardware-identifiers):

    - New-CMDuplicateHardwareIdGuid
    - Remove-CMDuplicateHardwareIdGuid
    - New-CMDuplicateHardwareIdMacAddress
    - Remove-CMDuplicateHardwareIdMacAddress