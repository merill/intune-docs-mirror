---
layout: Conceptual
title: Technical preview 2105 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2105
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2105.
ms.date: 2021-05-13T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: f1f63fea-a3cd-550a-9188-2ff4c52beb48
document_version_independent_id: 7dd1fb27-6bde-87d6-34b4-40f3e786ee61
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2105.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2105
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2105.md
platformId: 51b21764-0bcd-bafb-ee64-1a7a879f8df1
---

# Technical preview 2105 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2105. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Enhanced code editor

Building on improvements in Configuration Manager 2010 for [syntax highlighting and code folding](../../servers/manage/admin-console-tips#bkmk_syntax), you now have the ability to edit scripts in an enhanced editor. The new editor supports syntax highlighting, code folding, word wrap, line numbers, and find and replace. The new editor is available in the console wherever scripts and queries can be viewed or edited.

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

## Select VM size for CMG

When you deploy a cloud management gateway (CMG) with a [virtual machine scale set](../../clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets), you can now choose the virtual machine (VM) size. The following three options are available:

- **Lab**: [B2s](/en-us/azure/virtual-machines/sizes-b-series-burstable)
- **Standard**: [A2_v2](/en-us/azure/virtual-machines/av2-series). This option continues to be the default setting.
- **Large**: [D2_v3](/en-us/azure/virtual-machines/dv3-dsv3-series)

This control gives you greater flexibility with your CMG deployment. You can adjust the size for test labs or if you support large environments. For example, the smaller **Lab** size is ideal for testing with a smaller number of clients at less cost. For production deployments, either use the default **Standard** size or add more capacity with the **Large** size. For more information on how these options differ in cost for your region, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/).

For more general information on the CMG, see [CMG overview](../../clients/manage/cmg/overview).

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/find-help#product-feedback) with your thoughts on the feature.

1. [Set up a CMG](../../clients/manage/cmg/setup-cloud-management-gateway) with a virtual machine scale set.
2. On the **Settings** page of the wizard, change the **VM Size** to **Lab (B2s)**. By default, the CMG deploys with the **Standard (A2\_V2)** size.
3. Complete the wizard.

Configuration Manager deploys the CMG in Azure with the smaller VM size for your technical preview deployment in a lab.

If you've already deployed a CMG with a virtual machine scale set, you can [Modify the CMG](../../clients/manage/cmg/modify-cloud-management-gateway). On the **Settings** tab, change the VM size, and then select **OK** to save the changes. Configuration Manager redeploys the service in Azure to use the new VM size.

## Support Center dark and light themes

The [Support Center](../../support/support-center) tools now offer dark and light modes. Choose to use the system default color scheme, or override the system default by selecting either the dark or light theme.

### Try it out!

Try to complete the tasks. Then send [Feedback](/en-us/configmgr/core/understand/find-help#product-feedback) with your thoughts on the feature.

#### Set theme for OneTrace

**OneTrace** is the log viewer with Support Center. It works similarly to CMTrace, with many improvements. For more information, see [Support Center OneTrace](../../support/support-center-onetrace). To set the theme for OneTrace:

1. Open Support Center OneTrace.
2. Select **Window** then **Theme**.
3. Choose either the **System**, **Dark**, or **Light** theme.

![Screenshot of OneTrace with the Window, and Theme menus open](media/8218853-onetrace-theme.png)

#### Set theme for all other Support Center applications

For [all other Support Center applications](../../support/support-center-ui-reference), follow the instructions below to set the theme:

1. Open one of the following applications:
    - Support Center Client Tools
    - Support Center Client Data Collector
    - Support Center Viewer
    - Support Center Log File Viewer
2. In the upper left corner, select the arrow in the blue box to open the window menu and choose **Options**.
    - F4 is the keyboard shortcut to the **Options** menu.
3. In the **Theme** section, select either the **System**, **Dark**, or **Light** theme.
4. Select **Apply**.

## RBAViewer location change

RBAViewer has moved from `<installdir>\tools\servertools\rbaviewer.exe`. It's now located in the Configuration Manager console directory. After you install the console, RBAViewer.exe will be in the same directory. The default location is `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\rbaviewer.exe`.

## Updated client deployment prerequisite

The Configuration Manager client requires the Microsoft Visual C++ Redistributable component (`vcredist_x*.exe`). When you install the client, it automatically installs this component if it doesn't already exist. Starting in this release, it now uses the Microsoft Visual C++ 2015-2019 Redistributable version 14.28.29914.0. This version improves stability in Configuration Manager client operations.

For more information, see [Prerequisites for deploying clients to Windows computers](../../clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#components-automatically-downloaded-during-installation).

## Change to internet access requirements

To simplify the [internet access requirements](../../plan-design/network/internet-endpoints#updates-and-servicing) for Configuration Manager updates and servicing, this technical preview branch release downloads from `configmgrbits.azureedge.net`. This endpoint is already required, so should already be allowed through internet filters. With this change, the existing internet endpoint for technical preview releases is no longer required: `cmupdatepackppe.blob.core.windows.net`.

Tip

This change will also apply to the next current branch release. Since `configmgrbits.azureedge.net` is already a required endpoint, if you restrict internet access it shouldn't require any change. Before you install the next current branch release, confirm that the site system server that hosts the service connection point role can communicate with this internet endpoint. For more information, see [internet access requirements](../../plan-design/network/internet-endpoints#service-connection-point) for the service connection point.

## General known issues

### Known issue with a CMG deployed using classic cloud services

If you have a cloud management gateway (CMG) deployed using classic cloud services, after you upgrade the site to technical preview branch version 2105, the CMG web role repeatedly restarts and fails to start. The CMG status in the Configuration Manager console remains at **Upgrading** or **Provisioning**. You'll see entries similar to the following lines from the SMS\_CLOUD\_SERVICES\_MANAGER repeated in the **cloudmgr.log**:

```log
Deployment instance status for service <name> is BusyRole.
Deployment instance status for service <name> is RestartingRole.
```

This issue doesn't affect CMGs deployed with a virtual machine scale set.

### Configuration Manager console settings aren't saved

When you install the 2105 technical preview version of the Configuration Manager console, settings such as column changes, window size, and searches aren't saved. When you first open the upgraded console, it will appear as if it was never previously installed on the device. Any console settings made after installing the 2105 technical preview version of the Configuration Manager console will persist when you reopen it.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in technical preview version 2105.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets

#### Get-CMPersistentUserSettingsGroup

Use this cmdlet to get the list of site-wide settings that you've stored. These settings follow you on different devices.

For example, [Configuration Manager console notifications](../../servers/manage/admin-console-notifications) that are active or you've dismissed.

#### Remove-CMPersistentUserSettingsGroup

Use this cmdlet to reset your site-wide settings.

For example, you can restore [Configuration Manager console notifications](../../servers/manage/admin-console-notifications) that you've dismissed. After you run this cmdlet, and you restart the Configuration Manager console, you'll see all available notifications again.

### Modified cmdlets

#### Add-CMDeviceCollectionDirectMembershipRule

For more information, see [Add-CMDeviceCollectionDirectMembershipRule](/en-us/powershell/module/configurationmanager/Add-CMDeviceCollectionDirectMembershipRule).

**Bugs that were fixed**

Fixed an issue when trying to add thousands of devices as direct membership rules.

#### New-CMCloudManagementGateway

For more information, see [New-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/New-CMCloudManagementGateway).

**Breaking changes**

The **ServiceCertPassword** parameter is now required.