---
layout: Conceptual
title: Configure software inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/configure-software-inventory
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
description: Configure software inventory, and exclude folders from software inventory in Configuration Manager.
ms.date: 2018-01-03T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 766f46ec-945a-0c96-1e76-69edac0f2264
document_version_independent_id: 0e49c9e9-a954-8121-0c8e-b714d02bd8ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/configure-software-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/configure-software-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/configure-software-inventory.md
cmProducts: []
platformId: a39f1e60-0370-a357-537b-b7fa71161021
---

# Configure software inventory - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This procedure configures the default client settings for software inventory and applies to all the computers in your hierarchy. If you want to apply these settings to only some computers, create a custom device client setting and assign it to a collection. For more information about how to create custom device settings, see [How to configure client settings](../../deploy/configure-client-settings).

## To configure software inventory

1. In the Configuration Manager console, choose **Administration** &gt; **Client Settings** **Default Client Settings**.
2. On the **Home** tab, in the **Properties** group, choose **Properties**.
3. In the **Default Settings** dialog box, choose **Software Inventory**.
4. In the **Device Settings** list, configure the following values:

    - **Enable software inventory on clients** - From the drop-down list, select **True**.
    - **Schedule software inventory and file collection schedule** - Configures the interval at which clients collect software inventory and files.
5. Configure the client settings that you require. The [Software inventory](../../deploy/about-client-settings#software-inventory) section of the [About client settings](../../deploy/about-client-settings) article has a list of the client settings.

    Client computers will be configured with these settings when they next download client policy. To initiate policy retrieval for a single client, see [How to manage clients](../manage-clients).

    Tip

    Error code 80041006 in inventoryprovider.log means the WMI provider is out of memory. That is, the memory quota limit for a provider has been hit and inventory provider cannot continue. In this case, the inventory agent creates a report with 0 entries so no inventory items are reported.  A possible solution for this error would be to reduce the scope of the software inventory collection. In circumstances when the error occurs after limiting the inventory scope, increasing the [MemoryPerHost](https://techcommunity.microsoft.com/t5/ask-the-performance-team/memory-and-handle-quotas-in-the-wmi-provider-service/ba-p/373319) property defined in the [_ProviderHostQuotaConfiguration](/en-us/windows/win32/wmisdk/--providerhostquotaconfiguration) class can provide a solution.

## To exclude folders from software inventory

1. Using Notepad.exe, create an empty file named **Skpswi.dat**.
2. Right-click the **Skpswi.dat** file and click **Properties**. In the file properties for the Skpswi.dat file, select the **Hidden** attribute.
3. Place the **Skpswi.dat** file at the root of each client hard drive or folder structure that you want to exclude from software inventory.

Note

Software inventory will not inventory the client drive again unless this file is deleted from the drive on the client computer.