---
layout: Conceptual
title: Client health with co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-client-health
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
description: Maintain visibility of Configuration Manager client health from the Microsoft Intune admin center.
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: cc2400e8-064e-cb35-0dff-5cd99e7d40ec
document_version_independent_id: f41e208a-c5a7-d8a8-283e-c446cbdbad24
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-client-health.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-client-health
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-client-health.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c0439c36-80e3-415f-8e4c-6951e3f1b136
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/2812d699-d85f-4a7f-839d-44e218b35d24
platformId: 1183410a-86f6-d643-71d5-cc8e79cf257c
---

# Client health with co-management - Configuration Manager | Microsoft Learn

The health of your network is directly connected to the health of the devices moving in and out of it. Intune can communicate with an unhealthy client, even when it isn't on your network. Use co-management to combine this feature with Configuration Manager's ability to report back 98% of known healthy clients. Then you can detect, assess, and provide visibility across all clients in real time. Intune also adds the support needed for compliance upgrades across all connected clients.

In the following video, senior program manager Rob York and product marketing manager Locky Ainley discuss and demo client health with co-management:

## Benefits

Assessing client health is a top priority. System Center 2012 Configuration Manager added **CCMeval**. This utility is external to the Configuration Manager client. It provides client health monitoring and auto remediation. However, this reporting relies on a device being physically or virtually on your internal network. Co-management helps to address this issue.

With co-management, Intune can report on the client health state. It provides timestamp information for the validity of the data. This information tells you if your devices are healthy, able to connect, able to install apps, or can update to the required OS builds.

For a detailed overview of this feature, see this video from the [What's New in Configuration Manager](https://myignite.microsoft.com/archives/IG18-BRK3035) session at Ignite 2018.

When Configuration Manager provides device status that the client is installed, but it isn't, Intune can provide more information without needing to connect to the client. The device health info in Intune is easy to understand. If the status is anything other than **Healthy**, it gives recommendations and next steps to troubleshoot and fix it.

## Value proposition

With this feature, you now have an external data source with Intune. It allows you to determine next steps when troubleshooting a vast array of client issues. Now you don't need to create additional reports or use other tools to pull back client data.

When you have healthy clients, you have readily updated patch compliance. Better patch compliance means better security.

## Configure

To get started with this feature, use the following steps:

- Update devices to a supported version of Windows 10 or later.
- [Enable co-management](how-to-enable). You don't need to switch any workload to Intune.
- Update your Configuration Manager site and clients to a supported current branch version.

### Review Configuration Manager client health in Intune

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the menu under **Troubleshooting + support**, go to the **Troubleshoot** page.
3. Use the **Select user** option, find the specific device in the **Devices** list, and select it to open the device page.
4. Co-management information is shown at the bottom of the device page. This information includes the following fields for client health:

    - **Configuration Manager agent state**
    - **Last Configuration Manager agent check in time**

Tip

Intune-enrolled devices connect to the cloud service three times a day, approximately every eight hours.