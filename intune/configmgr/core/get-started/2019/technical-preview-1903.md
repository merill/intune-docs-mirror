---
layout: Conceptual
title: Technical preview 1903 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1903
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1903.
ms.date: 2019-04-03T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: c8663592-7c06-773d-9da0-b7718daa5930
document_version_independent_id: 601ca7cf-85e4-8669-400e-899aace9b72b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1903.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1903
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1903.md
platformId: 641da7e2-af04-e879-b0fc-04337fc22eed
---

# Technical preview 1903 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1903. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

**The following sections describe the new features to try out in this version:**

## Cloud services cost estimator

Some customers are concerned about the potential cost for attaching cloud services in Configuration Manager. This release introduces a new cost estimator tool in the Configuration Manager console. The tool uses the following data from your site database to estimate the cost of deploying the cloud management gateway:

- Aggregate, average client usage of management points and distribution points
- Azure pricing

In the Configuration Manager console, go to the **Monitoring** workspace, and select the **Cloud Management** node.

![Screenshot of cloud services usage estimation tool](media/3555774-cmg-cost-estimator.png)

By default, the tool shows data based on the following settings:

- Only laptop devices
- Client policy only, not content
- 30 days of client usage data
- 10% of the total clients simultaneously communicating with the cloud service

Select **Options** to include additional device types and content, adjust the number of CMG instances, adjust the percentage of simultaneous roaming clients, or change the Azure region.

#### Clients enabled for client services

The **Devices** value is what the tool uses for the cost estimates. It's initially the same as **Estimated devices**, based on the options that you specify. This value changes as you change the options. You can manually adjust this value by moving the slider control, or manually enter a value in the **Devices** field.

The **Estimated devices** value is based on the options that you specify. If you change the **Devices** value, this value doesn't change.

The value at the bottom far right of the slider control is the total number of applicable resources in the site database plus 20%. These devices are running the full Configuration Manager client (not MDM), and are active. The 20% buffer provides room in the slider control to estimate for future growth.

- **Laptops**: Devices capable of roaming with chassis type of portable, laptop, notebook, hand-held, docking station, or subnotebook
- **Servers**: Devices that aren't one of the laptop chassis types, and the Windows OS is a server type.
- **Desktops**: All other devices

For example, in the above screenshot, there are 42,267 total active laptops, servers, and desktops with the Configuration Manager client. Based on the configured options, 23,608 laptops can use cloud services. The administrator hasn't changed the **Devices** value to estimate future growth.

#### Client data consumption (per client/month)

The **MB/Device** value is an estimate based on usage data from the site for the past 30 days. By default, it starts with per-device policy only. In other words, per-device communication with the management point. Select **Options** to include content, or per-device communication with distribution points. You can manually adjust this value by moving the slider control, or manually enter a value in the **MB/Device** field.

Note

When you first update the site, it starts collecting usage data for this tool. It can take several weeks for the tool's estimates to be most useful. In the meantime, manually set your own value for **MB/Device**.

The **Estimated usage** value is based on the options that you specify. If you change the **MB/Device** value, this value doesn't change.

For example, in the above screenshot, 6,765 MB is a worst-case estimate, which provides an upper limit for the slider control. Based on the configured options and client usage data, the tool estimates 2,815 MB per client. The administrator manually changed the **MB/Device** value to 3,745 MB.

#### Total monthly cost estimate

This value is an estimated monthly cost for running CMG services in Azure. It's based on the specified options and the estimated number of devices.

Important

This value is a calculated estimate to help you make data-informed decisions for your environment.

When you set the number of devices and MB/device, the tool automatically sets a recommended number of CMG instances on the options page. For more information about CMG scale and cost, see [Cost for CMG](../../clients/manage/cmg/cost). The data egress cost is an estimate based on the percentage of roaming clients on the options page. By default, the percentage is 10%.

For example, you have 37,198 devices that can potentially use the CMG. If you configure the percentage at 25%, the tool estimates the monthly cost of 2,422.80 USD. This estimate is based on 9,300 devices simultaneously communicating with the CMG.

#### Monthly cost per device

This value is an average of the **Total monthly cost estimate** across all **Devices**. For example, if you estimate 25% simultaneous usage for the monthly cost estimate of 2,422.80 USD, that's calculated to 0.07 USD per client for 37,198 devices.

### Limitations

In this release, the Azure regions, currencies, and prices are fixed. The tool uses the following values:

| Location | Currency | VM instance cost | GB cost |
| --- | --- | --- | --- |
| West US | $ | 99.28 | 0.087 |
| West Europe | € | 80.03 | 0.074 |
| North Europe | £ | 70.73 | 0.065 |

Technical preview environments are intended for lab use and can't have more than 10 clients. Due to the low number of clients, this tool may show very low estimates. You can always manually adjust the values. Average client data consumption is typically between 1 to 3 GB per device.

## Use your distribution point as a local cache server for Delivery Optimization

You can now install Delivery Optimization In-Network Cache server on your distribution points. By caching this content on-premises, your clients can benefit from the Delivery Optimization feature, but you can help to protect WAN links.

This cache server acts as an on-demand transparent cache for content downloaded by Delivery Optimization. Use client settings to make sure this server is offered only to the members of the local Configuration Manager boundary group.

This cache is separate from Configuration Manager's distribution point content. If you choose the same drive as the distribution point role, it stores content separately.

Note

Delivery Optimization In-Network Cache server is an application installed on Windows Server that's still in development. It's tagged with a "beta" label in the Configuration Manager console.

### Prerequisites

- A distribution point running Windows Server 2012, Windows Server 2012 R2, Windows Server 2016, or Windows Server 2019.
- The distribution point requires internet access to the Microsoft cloud. The specific URLs can vary depending upon the specific cloud-enabled content.
- Clients running Windows 10 version 1709 or later

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the properties of the distribution point role, on the **General** tab, configure the following settings:

    1. Enable the option to **Enable this distribution point to be used as a Delivery Optimization In-Network Cache server**
    2. **Local drive to be used**: Select the disk to use for the cache. **Automatic** is the default value, which uses the disk with the most free space.
    3. **Disk space**: Select the amount of disk space to reserve in GB or a percentage of the total disk space. By default, this value is 100 GB.
    4. **Retain cache when disabling the in-network cache server**: If you remove the cache server, and you enable this option, the server keeps the cache's content on the disk.
2. In client settings, in the **Delivery Optimization** group, configure the setting to **Enable devices managed by Configuration Manager to use Delivery Optimization In-Network Cache servers for content download**.

### Verify

When clients download cloud-managed content, they use Delivery Optimization from the cache server installed on your distribution point. Cloud-managed content includes the following types:

- Microsoft Store apps
- Windows features on demand, such as languages
- If you enable [Windows Update client policies](../../../sum/deploy-use/integrate-windows-update-client-policies): Windows 10 feature and quality updates
- For [co-management workloads](../../../comanage/workloads):
    - Windows Update client policies: Windows 10 feature and quality updates
    - Office Click-to-Run apps: Office apps and updates
    - Client apps: Microsoft Store apps and updates
    - Endpoint Protection: Windows Defender definition updates

On Windows 10 version 1809 or later, verify this behavior with the **Get-DeliveryOptimizationStatus** Windows PowerShell cmdlet. In the cmdlet output, review the **BytesFromCacheServer** value.

If the cache server returns any HTTP failure, the Delivery Optimization client falls back to the original cloud source.

## Reclaim lock for editing task sequences

If the Configuration Manager console stops responding, you can be locked out of making further changes until the lock expires after 30 minutes. This lock is part of the Configuration Manager SEDO (Serialized Editing of Distributed Objects) system. For more information, see [Configuration Manager SEDO](../../../develop/core/understand/sedo).

Based on your feedback, now you can clear your lock on a task sequence. This action only applies to your user account that has the lock, and on the same device from which the site granted the lock. When you attempt to access a locked task sequence, you can now **Discard Changes**, and continue editing the object. These changes would be lost anyway when the lock expired.

## Drill through required updates

Based on your feedback, you can now drill through compliance statistics to see which devices require a specific software update. To view the device list, you need permission to view updates and the collections the devices belong to.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Go to one of the following places in the Configuration Manager console:

    - **Software Library** &gt; **Software Updates** &gt; **All Software Updates**
    - **Software Library** &gt; **Windows 10 Servicing** &gt; **All Windows 10 Updates**
    - **Software Library** &gt; **Office 365 Client Management** &gt; **Office 365 Updates**
2. Select any update that is required by at least one device.
3. Look at the **Summary** tab and find the pie chart under **Statistics**.
4. Select the **View Required** hyperlink next to the pie chart to drill down into the device list.
5. This action takes you to a temporary node under **Devices** where you can see the devices requiring the update. You can also take actions for the node such as creating a new collection from the list.

## Improvement to task sequence media creation

Based on your feedback, when you create task sequence media, Configuration Manager doesn't add an autorun.inf file. This file is commonly blocked by antimalware products. For more information on the AutoRun feature of Windows, see [Creating an AutoRun-enabled CD-ROM Application](/en-us/windows/desktop/shell/autoplay).

You can still include the file if necessary for your scenario. When you create task sequence media in the Configuration Manager console, on the **Media Type** page of the wizard, select the option to **Include autorun.inf file on media**. By default, this option is disabled.

## Known issues

### Client health dashboard

In this version of technical preview, the [client health dashboard](technical-preview-1901#bkmk_health) doesn't display any data.