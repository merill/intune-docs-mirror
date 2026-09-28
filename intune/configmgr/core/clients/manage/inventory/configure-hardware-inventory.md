---
layout: Conceptual
title: Configure hardware inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/configure-hardware-inventory
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
description: Set up hardware inventory for all clients or for a collection in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 777c8d9d-88be-7d09-f8ee-58a688f2cfc6
document_version_independent_id: 725091b6-81de-2084-07a7-f327eb12634f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/configure-hardware-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/configure-hardware-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/configure-hardware-inventory.md
cmProducts: []
platformId: 916f0179-fa58-c0ac-91fb-c9147ab4023b
---

# Configure hardware inventory - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This procedure configures the default client settings for hardware inventory and will apply to all the clients in your hierarchy. If you want these settings to apply to only some clients, create a custom device client setting and assign it to a collection that contains the devices that you want to use hardware inventory. See [How to configure client settings](../../deploy/configure-client-settings).

Note

If a client device receives hardware inventory settings from multiple sets of client settings, then the hardware inventory classes from each set of settings will be merged when the client reports hardware inventory. Additionally, not checking a class in a custom client setting with a higher priority doesn't disable the client from inventorying that class.

To disable a specific hardware inventory class on a majority of systems except a few, the class needs to be unchecked in the default client settings. Then create a custom client setting to enable the class, and deploy it to the target systems.

### To configure hardware inventory

1. In the Configuration Manager console, choose **Administration** &gt; **Client Settings** &gt; **Default Client Settings**.
2. On the **Home** tab, in the **Properties** group, choose **Properties**.
3. In the **Default Settings** dialog box, choose **Hardware Inventory**.
4. In the **Device Settings** list, configure the following:

    - **Enable hardware inventory on clients** - Select **Yes**.
    - **Hardware inventory schedule** - Click **Schedule** to specify the interval at which clients collect hardware inventory.
5. Configure other [hardware inventory client settings](../../deploy/about-client-settings#hardware-inventory) that you require.

Client devices will be configured with these settings when they next download client policy. To initiate policy retrieval for a single client, see [How to manage clients](../manage-clients).