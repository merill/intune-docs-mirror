---
layout: Conceptual
title: Technical preview 1902.2 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1902-2
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1902.2.
ms.date: 2019-02-19T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: aff5b907-1939-d411-1968-4a6cb343bcab
document_version_independent_id: cd5d9546-db05-d9eb-4823-7ad585b6ab6c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1902-2.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1902-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1902-2.md
platformId: 266c82b1-201a-4ec4-ccfb-1d36b95021c8
---

# Technical preview 1902.2 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1902.2. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

**The following sections describe the new features to try out in this version:**

## Additional languages for Microsoft 365 updates

Configuration Manager now supports all supported languages for Microsoft 365 client updates. The update workflow now separates the 38 languages for **Windows Update** from the 103 languages for **Microsoft 365 Client Update**.

To select the necessary languages, use the **Language Selection** page in the following locations:

- Create Automatic Deployment Rule Wizard
- Deploy Software Updates Wizard
- Download Software Updates Wizard
- Automatic Deployment Rule Properties

## Integration with analytics for Microsoft 365 Apps for enterprise readiness

Use Configuration Manager to identify devices with high confidence that are ready to upgrade to Microsoft 365 Apps for enterprise. By integrating with Office analytics, it provides insights into any potential compatibility issues with Office add-ins and macros used in your environment. Then use Configuration Manager to deploy Office to ready devices.

The existing [Office 365 client management dashboard](../../../sum/deploy-use/office-365-dashboard#bkmk_o365_readiness) now includes a new tile, **Office 365 ProPlus Upgrade Readiness**. This tile is a bar chart of devices in the following states:

- Not assessed
- Ready to upgrade
- Needs review

Select a state to drill-through to a device list. This readiness report shows more detail about devices. It includes columns for the compatibility state of both Office add-ins and macros.

### Prerequisites

- Enable hardware inventory in client settings. For more information, see [How to configure hardware inventory](../../clients/manage/inventory/configure-hardware-inventory).
- The device needs connectivity to the Office content delivery network (CDN) to download an add-in readiness file. For more information, see [Content delivery networks](/en-us/office365/enterprise/content-delivery-networks). If the device can't download this file, the add-ins state is *Needs review*.

    Note

    No data is sent to Microsoft for this feature.

### Detailed macro readiness

By default, the scanning agent looks at the most recently used (MRU) files list on each device. It counts the files in this list that support macros. These files include the following types:

- Macro-enabled Office file formats, such as Excel macro-enabled workbooks (.xlsm) or Word macro-enabled document (.docm)
- Older Office formats that don't indicate whether there's macro content. For example, an Excel 97-2003 workbook (.xls).

If you need a more detailed evaluation, deploy the **Readiness Toolkit**. This tool analyzes the code within a macro file. It checks if there are any potential compatibility concerns. For example, the file uses a function that changed in a more recent version of Office. After you run the Readiness Toolkit, Configuration Manager can use its results. This additional data enhances the device readiness calculation.

For more information, see [Use the Readiness Toolkit to assess application compatibility for Microsoft 365 Apps for enterprise](/en-us/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps).

## Improvement to phased deployment success criteria

Specify additional criteria for the success of a phase in a phased deployment. Instead of only a percentage, this criteria can now also be the number of devices successfully deployed. This option is useful when the size of the collection is variable, and you have a specific number of devices to show success before moving to the next phase.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Create a phased deployment for a [task sequence](../../../osd/deploy-use/create-phased-deployment-for-task-sequence), [application](../../../osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/mem/configmgr/app/toc.json&amp;bc=/mem/configmgr/app/breadcrumb/toc.json), or [software update](../../../osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/mem/configmgr/sum/toc.json&amp;bc=/mem/configmgr/sum/breadcrumb/toc.json).
2. On the Settings page of the wizard, select the following option as the criteria for success of the first phase: **Number of devices successfully deployed**. Then specify a number between 1 and 100,000.
3. Complete the wizard.

To monitor the deployment, use the **Phased Deployment Status** action in the Deployments node. For more information, see [Monitor phased deployments](../../../osd/deploy-use/manage-monitor-phased-deployments#bkmk_monitor). The **SMS\_PhasedDeployment.log** on the site server shows the criteria evaluation.

Tip

- Use this setting on collections that may increase in the number of members. If the collection reduces in size, this criteria may become greater than the total membership.
- Don't set this value to be significantly greater than the current size of the collection.

## Improvement to enhanced HTTP

You can now enable [enhanced HTTP](../../plan-design/hierarchy/enhanced-http) per primary site or for the central administration site. This change provides better support for features that require it. For example, [app approvals via email](../../../apps/deploy-use/app-approval#bkmk_email-approve) or [viewing recently connected consoles](technical-preview-1901#bkmk_console).

To enable enhanced HTTP for the central administration site:

1. In the Configuration Manager console, go to the **Administration** workspace.
2. Expand **Site Configuration** and select the **Sites** node.
3. Select the central administration site server, and choose **Properties** in the ribbon.
4. On the General tab, select the option to **Use Configuration Manager-generated certificates for HTTP site systems**.

Tip

This action only enables enhanced HTTP for the SMS Provider roles at the central administration site. It's not a global setting that applies to all sites in the hierarchy. To enable enhanced HTTP at a primary site, see [Configure the site](../../plan-design/hierarchy/enhanced-http#configure-the-site).