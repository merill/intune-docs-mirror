---
layout: Conceptual
title: Product lifecycle dashboard - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/product-lifecycle-dashboard
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
description: View the Microsoft Lifecycle Policy with the product lifecycle dashboard in Configuration Manager.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 64a765ac-1df0-728e-93e7-521618de72b0
document_version_independent_id: 3d0c4362-2e53-2b5b-4c62-7041b767c98f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/product-lifecycle-dashboard.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/product-lifecycle-dashboard
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/product-lifecycle-dashboard.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2404adc4-b5e4-2e3e-49c0-d79949031a1e
---

# Product lifecycle dashboard - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the Configuration Manager product lifecycle dashboard to view the Microsoft Lifecycle Policy. The dashboard shows the state of the Microsoft Lifecycle Policy for Microsoft products installed on devices managed with Configuration Manager. It also provides you with information about Microsoft products in your environment, supportability state, and support end dates. Use the dashboard to understand the availability of support for each product. This information helps you plan for when to update the Microsoft products you use before their current end of support is reached.

For more information, see the [Microsoft Lifecycle Policy](/en-us/lifecycle).

## Prerequisites

To see data in the product lifecycle dashboard, the following components are required:

- Install Internet Explorer 9 or later on the computer that runs the Configuration Manager console.
- To get updates for the data on this dashboard, the service connection point must be online. If the service connection point is in offline mode, synchronize it regularly. For more information, see [About the service connection point](../../../servers/deploy/configure/about-the-service-connection-point).
- In version 2111 and earlier: Configure and synchronize the asset intelligence synchronization point. The dashboard uses the asset intelligence catalog as metadata for product titles. Configuration Manager compares this metadata against inventory data in your hierarchy. For more information, see [Configure asset intelligence in Configuration Manager](configuring-asset-intelligence).

    Note

    Starting in version 2203, the product lifecycle dashboard isn't dependent on the asset intelligence synchronization point.
- [Enable asset intelligence hardware inventory classes](configuring-asset-intelligence#BKMK_EnableAssetIntelligence). The lifecycle dashboard depends on these classes. The dashboard won't display data until clients scan for and return hardware inventory.

## Use the product lifecycle dashboard

To access the lifecycle dashboard in the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Asset Intelligence**, and select the **Product Lifecycle** node.

Based on inventory data the site collects from managed devices, the dashboard displays information about all current products. However, the information displayed for operating systems and SQL Server is limited to the following versions:

- Windows Server 2008 and later
- Windows XP and later
- SQL Server 2008 and later

Note

The data in the dashboard is based on the site the Configuration Manager console connects to. If the console connects to your top-tier site, you see data for the entire hierarchy. When connected to a child primary site, only data from that site displays.

### Product lifecycle dashboard

[![Screenshot of the product lifecycle dashboard in the console.](media/product-lifecycle-dashboard.png)](media/product-lifecycle-dashboard.png#lightbox)

Change the view by selecting one of the following options from the **Product category** list:

- **All**: View all products together
- **Windows Client**: View Windows client OS versions
- **Windows Server**: View Windows server OS versions
- **Database**: View SQL Server versions
- **Configuration Manager**: View Configuration Manager versions
- **Microsoft Office**: View information for installed versions of Office 2003 through Office 2016

The dashboard has the following tiles:

- **Top 5 products past end-of-support**: This tile is a consolidated data view of products found in your environment past their end-of-support. The graph shows installed software that's expired when compared against the support lifecycle for operating systems and SQL Server products.
- **Top 5 products nearing end-of-support**: This tile is a consolidated data view of products found in your environment that are nearing end-of-support in next 18 months. The graph shows installed software that's within 18 months of end-of-support when compared against the support lifecycle for operating systems and SQL Server products.

    Starting in version 2103, use the time slider to control the timeframe for this tile. The default is 18 months, but you can adjust it from 1 to 36 months.

    ![Product lifecycle dashboard highlighting new timescale control at 33 months.](media/8160460-product-lifecycle-timescale.png)
- **Lifecycle data for installed products**: This tile gives you a general idea of when a product transitions from supported to the expired state. The chart provides a breakdown of the number of clients where the product is installed, the support availability state, and a link to learn more about the next steps to take. The following information is included in the chart:

    - Support time remaining
    - Number in environment
    - Mainstream support end date
    - Extended support end date
    - Next steps

Starting in version 2103, the dashboard also has a subnode, **All Product Lifecycle Data**. You can sort and filter the product lifecycle information, which gives you multiple ways to view it. When you select a product, you can **View devices** for that product. From the list of devices, you can create a direct membership collection. Use this action to deploy the latest software versions to these collections so that the devices are kept current.

Important

The information shown in this dashboard is provided for your convenience and only for use internally within your company. You should not solely rely on this information to confirm compliance. Be sure to verify the accuracy of the information provided to you, along with availability of support information by visiting the [Microsoft Lifecycle Policy](/en-us/lifecycle).

## Reporting

Other reports are available as well. In the Configuration Manager console, go to the **Monitoring** workspace, expand **Reporting**, and expand **Reports**. The following reports are added under the category **Asset Intelligence**:

- **Lifecycle 01A - Computers with a specific software product**: View a list of computers on which a specified product is detected.
- **Lifecycle 02A - List of machines with expired products in the organization**: View computers that have expired products on them. You can filter this report by product name.
- **Lifecycle 03A - List of expired products found in the organization**: View details for products in your environment that have expired lifecycle dates.
- **Lifecycle 04A - General Product Lifecycle overview**: View a list of product lifecycles. Filter the list by product name and days to expiration.
- **Lifecycle 05A - Product lifecycle dashboard**: This report includes similar information as the in-console dashboard. Select a category to view the count of products in your environment, and the days of support remaining.

For more information, see [List of reports](../../../servers/manage/list-of-reports#asset-intelligence).