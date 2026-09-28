---
layout: Conceptual
title: Surface Device Dashboard - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/surface-device-dashboard
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
description: Review information about Surface devices using the dashboard.
ms.date: 2021-11-15T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 770c8294-6e55-7b97-774f-4b8f17510304
document_version_independent_id: ce1a6982-58d5-cd3b-c4bd-1c0af737ce54
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/surface-device-dashboard.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/surface-device-dashboard
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/surface-device-dashboard.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: 2744119b-2491-a725-31a6-73dfee9a63b6
---

# Surface Device Dashboard - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Surface device dashboard gives you information about Surface devices found in your environment at a single glance.

## How to open

To open the Surface device dashboard, use the following steps:

1. Open the Configuration Manager console.
2. Select the **Monitoring** workspace.
3. To load the dashboard, select the **Surface Devices** node.

![An example view of the Surface device dashboard.](media/surface-device-dashboard.png)

## Review information

The Surface device dashboard shows three graphs:

- **Percent of Surface devices**: The percentage of Surface devices throughout your environment.

    ![Percent of Surface devices graph.](media/percent-surface-devices.png)
- **Surface Models**: The number of devices per Surface model. Hover over a graph section to see the percentage of Surface devices for that model.

    ![Surface models graph.](media/surface-models-hover.png)

    - Select a graph section to go through to a device list for that model.

        ![Surface model device list.](media/surface-model-device-list.png)
- **Top five firmware versions**: The top five firmware models in your environment. Hover over a graph section to see the number of Surface devices with that firmware version. Select a graph section to go through to a device list.

    ![Surface top five firmware versions graph.](media/surface-firmware-hover.png)