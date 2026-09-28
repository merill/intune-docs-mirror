---
layout: Conceptual
title: Manage update catalogs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/updates-publisher-catalogs
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
description: Manage software update catalogs for System Center Updates Publisher
ms.date: 2017-04-29T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 319506e0-82d7-7c78-4c09-ee68ddae12fa
document_version_independent_id: 077c840f-115a-866b-3296-15f3641ff610
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/tools/updates-publisher-catalogs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/tools/updates-publisher-catalogs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/tools/updates-publisher-catalogs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 32dc92ff-02d5-8320-2ad3-49a00c187c1d
---

# Manage update catalogs - Configuration Manager | Microsoft Learn

*Applies to: System Center Updates Publisher*

Use the **Catalogs** **Workspace** to manage software update catalogs. This includes adding new catalogs, managing existing catalog subscriptions, and importing information about the updates from a catalog to the Updates Publisher repository.

Software update catalogs contain information about related updates that are created by organizations other than Microsoft. Other organizations include your own organization and third-party software vendors that have registered their catalogs with Microsoft. Registered catalogs from software vendors are called *partner catalogs*. Catalogs that you create, and that are not registered with Microsoft, are called *user* catalogs.

## Add software update catalogs

You must add an update catalog to Updates Publisher before you can manage the updates that it contains. When you add a catalog, Updates Publisher:

- Creates a subscription to that catalog, so it can check for updates to that catalog.
- Adds the catalog to a list in the **My Software Update Catalogs** window of the **Catalogs Workspace**.

Information about each subscribed catalog is available in the console. Information includes the download URL or location, the name of the company or organization who created the catalog, and when it was last imported or modified.

Updates Publisher can automatically check your subscriptions for changes each time it starts. This is configured as an [Advanced option](updates-publisher-options#advanced). When configured, Updates Publisher references the download URL or location information for the subscription and alerts you when there are changes to the catalog that were made since the last time you imported it to the repository.

To manually check for a catalog update, select the catalog from the **My Software Update Catalogs** list and then choose **Refresh** from the ribbon.

In addition to adding catalogs, and viewing information about subscribed catalogs, you can:

- **Edit** information for *user* catalogs.
- **Delete** (remove) a catalog from Updates Publisher.
- **Import** updates from a catalog into the Updates Publisher repository. When you import updates, you import all updates contained in that catalog. You can then view the updates in the Updates workspace where you can then select and publish updates to your update server.

Note

Deleting a catalog from Updates Publisher results in the updates in that catalog being removed from your repository. This does not affect the updates you have published to your update server. To remove updates from your update server that are no longer in your repository, see [Expire unreferenced software updates](updates-publisher-options#expire-unreferenced-software-updates).

## Manage update catalogs

You can view the list catalogs you have imported in the **My Software Update Catalogs** window of the **Catalogs Workspace**. From this workspace you can:

- **Add a partner catalog:** Use one of the following to find new partner catalogs:

    - In the console, go to **Updates Workspace** &gt; **Overview**. In the **Getting Started** window, choose **Add Partner Software Updates Catalogs**.
    - In the console, go to **Catalogs Workspace** &gt; **My Catalogs**. Then, from the ribbon, choose **Add Catalogs**.
- **Add a user catalog:** In the console, go to **Catalogs Workspace** &gt; **My Catalogs**. Then, from the ribbon, choose **Add Catalogs**. In addition to the location of the .cab file, you must specify a Publisher, Name, and Description to identify the catalog.
- **Check for updates to catalogs:** Select one or more catalogs and then choose **Refresh** from the ribbon.
- **Edit a user catalog:** Select a *user* catalog and then choose **Edit** from the ribbon. You can then modify the user defined properties.
- **Delete catalogs:** Select one or more catalogs and then choose **Remove** from the ribbon. This removes the catalog, your subscription, and the updates from those catalogs from your Updates Publisher repository.
- **Add updates from a catalog to your repository**: Choose **Import** from the ribbon to start the **Import Catalog** wizard. For more infomration, see Import updates

## Import updates

When you import a catalog, Updates Manager adds the updates from that catalog to the Updates Publisher repository. After updates are imported, you can publish them to your update server to make them available to managed devices.

### To import updates

1. To start the **Import Catalog** wizard, choose **Import** from the Ribbon in one of the following workspaces:

    - Catalogs Workspace
    - Updates Workspace
2. On the **Import Type** page, select one or more catalogs you've added to Updates Publisher, or specify a path to a catalog you have not yet added as a subscription. Chose **Next** to view the summary screen, and when ready, choose **Next** to start the import.
3. On the **Security Warning – Catalog Validation** window, review the catalog certificate, and when ready, chose **Accept** to import the updates.

Caution

Accept updates only from publishers that you trust. Software updates from publishers who are not trusted can potentially harm client computers when scanning for updates.

If you no longer trust a publisher, remove that publisher from the trusted publishers list. To find more information about accepting catalogs, click **Tell Me More** in the **Security Warning – Catalog Validation** dialog box.

    If you choose to always accept catalogs from a publisher, that publisher is added to the [trusted publishers list](updates-publisher-options#trusted-publishers). You can review and edit this list as an Updates Publisher option.
4. Import skips import of an update when the update is already in the repository and one of the following is true:

    - The update is unchanged from the last time it was imported.
    - The update has been edited and has a new digital hash. Editing an update prevents a new update from overwriting the original as doing so would overwrite changes you might have deployed.
5. On the **Confirmation** page review the import results.
6. Click **Close** to complete the wizard. You can now view the updates for this catalog in the Updates Workspace.