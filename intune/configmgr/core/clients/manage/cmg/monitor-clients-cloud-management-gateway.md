---
layout: Conceptual
title: Monitor the CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/monitor-clients-cloud-management-gateway
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
description: Monitor clients and network traffic through the cloud management gateway (CMG).
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 900fc69f-f7c4-95f9-fee2-eae88adca763
document_version_independent_id: 9f8b263b-8f05-0c51-c9b4-615fa306631e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/monitor-clients-cloud-management-gateway.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/monitor-clients-cloud-management-gateway
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/monitor-clients-cloud-management-gateway.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: a0b9d7fa-7f5f-d5e8-76ad-fd76b66dc9c8
---

# Monitor the CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After the cloud management gateway (CMG) is running and clients are connecting through it, you can monitor clients and network traffic. Monitor the service to make sure its performance is optimal.

## Monitor clients

Clients connected through the CMG appear in the Configuration Manager console the same way on-premises clients do. For more information, see [how to monitor clients](../monitor-clients).

## Monitor traffic in the console

Monitor traffic on the CMG using the Configuration Manager console:

1. Go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Management Gateway** node.
2. Select the CMG in the list pane.
3. View the traffic information in the details pane for the CMG connection point and the site system roles it connects to. These statistics show the client requests coming into these roles. The requests include policy, location, registration, content, inventory, and client notifications.

## Monitor content

Monitor content that you distribute to a CMG the same as with any other distribution point. For more information, see [Monitor content](../../../servers/deploy/configure/monitor-content-you-have-distributed).

When you view the list of CMGs in the console, you can add more columns to the list. For example, the **Storage egress (GB)** column shows the amount of data that clients downloaded from the service in the last 30 days.

## Monitor logs

The following table lists the log files that contain information related to the cloud management gateway.

| Log name | Description | Computer with log file |
| --- | --- | --- |
| CloudMgr.log | Records details about deploying the cloud management gateway service, ongoing service status, and use data associated with the service. To configure the logging level, edit the **Logging level** value in the following registry key: `HKLM\SOFTWARE\ Microsoft\SMS\COMPONENTS\ SMS_CLOUD_ SERVICES_MANAGER` | The *installdir* folder on the primary site server or CAS. |
| CMGSetup.log ^Note 1^ | Records details about the second phase of the cloud management gateway deployment (local deployment in Azure). To configure the logging level, use the setting **Trace level** (**Information** (Default), **Verbose**, **Error**) on the **Azure portal\Cloud services configuration** tab. | The **%approot%\logs** on your Azure server, or the SMS/Logs folder on the site system server |
| CMGService.log ^Note 1^ | Records details about the cloud management gateway service core component in Azure. To configure the logging level, use the setting **Trace level** (**Information** (Default), **Verbose**, **Error**) on the **Azure portal\Cloud services configuration** tab. | The **%approot%\logs** on your Azure server, or the SMS/Logs folder on the site system server |
| SMS\_Cloud\_ProxyConnector.log | Records details about setting up connections between the cloud management gateway service and the cloud management gateway connection point. | Site system server |
| CMGContentService.log ^Note 1^ | When you enable a CMG to also serve content from Azure storage, this log records the details of that service. | The **%approot%\logs** on your Azure server, or the SMS/Logs folder on the site system server |

- For troubleshooting deployments, use **CloudMgr.log** and **CMGSetup.log**
- For troubleshooting service health, use **CMGService.log** and **SMS\_Cloud\_ProxyConnector.log**.
- For troubleshooting client traffic, use **CMGService.log** and **SMS\_Cloud\_ProxyConnector.log**.

#### Note 1: Logs synchronized from Azure

These are local Configuration Manager log files that cloud service manager syncs from Azure storage every five minutes. The cloud management gateway pushes logs to Azure storage every five minutes. So the maximum delay is 10 minutes. Verbose switches affect both local and remote logs. The actual file names include the service name and role instance identifier. For example, CMG-*ServiceName*-*RoleInstanceID*-CMGSetup.log. These log files are synced, so you don't need to RDP to the cloud management gateway to obtain them, and that option isn't supported.

## Cloud management dashboard

The cloud management dashboard provides a centralized view for CMG usage. It also displays data about cloud users and devices.

In the Configuration Manager console, go to the **Monitoring** workspace. Select the **Cloud Management** node, and view the dashboard tiles.

The following screenshot shows the section of the cloud management dashboard specific for the CMG:

[![Cloud management dashboard tiles CMG traffic and Current online clients.](media/cloud-management-dashboard-cmg.png)](media/cloud-management-dashboard-cmg.png#lightbox)

## Connection analyzer

To aid troubleshooting, use the CMG connection analyzer for real-time verification. The in-console utility checks the current status of the service, and the communication channel through the CMG connection point to any management points that allow CMG traffic.

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Cloud Services** and select the **Cloud management gateway** node.
2. Select the target CMG instance, and then select **Connection analyzer** in the ribbon.
3. In the CMG connection analyzer window, select one of the following options to authenticate with the service:

    1. **Microsoft Entra user**: Use this option to simulate communication the same as a cloud-based user identity signed in to a Microsoft Entra joined Windows device. Select **Sign In** to securely enter the credentials for a Microsoft Entra user account.
    2. **Client certificate**: Use this option to simulate communication the same as a Configuration Manager client with a [client authentication certificate](configure-authentication#pki-certificate).
4. Select **Start** to start the analysis. The analyzer window displays the results. Select an entry to see more details in the Description field.

![Example output for the cloud management gateway (CMG) connection analyzer.](media/cmg-connection-analyzer.png)

## Set up outbound traffic alerts

Outbound traffic alerts help you know when network traffic approaches a 14-day threshold level. When you create the CMG, you can set up traffic alerts. If you skipped that part, you can still set up the alerts after the service is running. Adjust the alert settings at any time.

You can also configure thresholds for the amount of data that you want to store on the CMG and that clients download. Use alerts for these thresholds to help you decide when to stop or delete the cloud service, adjust the content that you store on the CMG, or modify which clients can use the service.

1. Go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Management Gateway** node.
2. Select the CMG in the list pane, and then select **Properties** in the ribbon.
3. Go to the **Alerts** tab to enable the threshold and alerts:

    - Specify the **14-day data threshold for outbound data transfer** in gigabytes (GB). This threshold helps you to monitor the amount of data that transfers from the CMG to clients every two weeks. By default, this threshold is approximately **10 TB**. The default value is `10,000` GB. The site raises warning and critical alerts when transfers reach values that you define. By default, these alerts occur at 50% and 90% of the threshold.
    - If the CMG is content-enabled, also specify a **storage alert threshold**. This threshold sets an upper limit on the amount of content to store on the CMG. By default, this threshold is approximately **2 TB**. The default value is `2,000` GB. Configuration Manager generates warning and critical alerts when the remaining free space reaches the levels that you specify. By default, these alerts occur at 50% and 90% of the threshold.

Note

Alerts for the CMG depend on usage statistics from Azure, which can take up to 24 hours to become available. For more information about Storage Analytics for Azure, see [Storage Analytics](/en-us/azure/storage/common/storage-analytics).

In an hourly cycle, the primary site that monitors the CMG downloads transaction data from Azure. It stores this transaction data in the `CloudDP-<ServiceName>.log` file on the site server. Configuration Manager then evaluates this information against the storage and transfer quotas for each CMG. When the transfer of data reaches or exceeds the specified volume for either warnings or critical alerts, Configuration Manager generates the appropriate alert.

Because the site downloads information about data transfers from Azure every hour, the usage might exceed a warning or critical threshold before Configuration Manager can access the data and raise an alert.

## Stop CMG when it exceeds threshold

Configuration Manager can stop a CMG service when the total data transfer goes over your limit. Use alerts to trigger notifications when the usage reaches warning or critical levels. To help reduce any unexpected Azure costs because of a spike in usage, this option turns off the cloud service.

Important

Even if the service isn't running, there are still costs associated with the cloud service. Stopping the service doesn't eliminate all associated Azure costs. To remove all cost for the cloud service, [delete the CMG](modify-cloud-management-gateway#delete-the-service).

When you stop the CMG service, internet-based clients can't communicate with Configuration Manager.

The total data transfer (egress) includes data from the cloud service and storage account. This data comes from the following flows:

- CMG to client
- CMG to site, including CMG log files
- If you enable CMG for content, storage account to client

For more information on these data flows, see [CMG ports and data flow](data-flow).

The storage alert threshold is separate. That alert monitors the capacity of your Azure storage instance.

When you select the CMG instance in the **Cloud Management Gateway** node in the console, you can see the total data transfer in the details pane.

Configuration Manager checks the threshold value every six minutes. If there's a sudden spike in usage, Configuration Manager can take up to six minutes to detect that it exceeded the threshold and then stop the service.

### Process to stop the cloud service when it exceeds threshold

1. Set up outbound traffic alerts.
2. On the **Alerts** tab of the CMG properties window, enable the option to **Stop this service when the critical threshold is exceeded**.

To test this feature, temporarily reduce one of the following values:

- **14-day threshold for outbound data transfer (GB)**. The default value is `10000`.
- **Percentage of threshold for raising Critical alert**. The default value is `90`.