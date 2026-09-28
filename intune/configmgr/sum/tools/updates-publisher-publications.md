---
layout: Conceptual
title: Manage publications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/updates-publisher-publications
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
description: Manage groups of software updates as a publication with System Center Updates Publisher
ms.date: 2017-04-29T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 2ae567e3-2b04-4d92-8386-f90baa469d6c
document_version_independent_id: b82b1dfd-0064-44c2-2729-71be1a451724
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/tools/updates-publisher-publications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/tools/updates-publisher-publications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/tools/updates-publisher-publications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: c8766620-e8aa-5f67-cba5-dea5a72da529
---

# Manage publications - Configuration Manager | Microsoft Learn

*Applies to: System Center Updates Publisher*

You can use publications to manage groups of updates and bundles as a single object. This includes publishing the updates to a management server and exporting the publication as group for use with another install of Updates Publisher.

## Create publications

Publications are created two ways:

- When you manage updates and bundles in the **Updates Workspace**, you can [assign](manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication) them to a new publication that is created at that time.
- In the **Publications Workspace,** you can use the **Create** button on the **Publication** tab of the ribbon. This method lets you create a publication for future use. Later, when you assign updates, you can use this publication.

## Rename a publication

To rename a publication, select the publication from within the **Publications Workspace**, and then on the **Publication** tab of the ribbon, choose **Edit**.

## Change the publication type of updates in a publication

From the **Publication Workspace**, you can modify the **publication type** of updates and bundles that are assigned to a publication.

1. Select the publication that contains the updates you want to modify, and then select one or more update or bundles from the **All &lt;publication name&gt; member updates** list.
2. Next, on the **Home** tab, choose one of the following options. The options that are available depend on the publication type of the updates you have selected.

    - **Automatic**
    - **Full Content**
    - **Metadata only**

After making a change, you might need to refresh the publication view to see the new values.

For information about the different publication types, see [Assign updates and bundles to a publication](manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication).

Tip

When you set the publication type of a bundle, all the software updates in that bundle are published with the publication type of that bundle.

## Remove updates from a publication

To remove updates or bundles from a publication, in the **Publications Workspace** select the publication you want to modify, and then select the updates and bundles you want to remove. Next, on the **Home** tab of the ribbon, choose **Remove**.

After updates are removed from a publication, they remain available in the Updates Publisher repository.

## Publish publications

When you publish updates and bundles, Updates Publisher adds information about those updates and bundles (metadata) and possibly the binaries for the updates (full content), to an update server for deployment to devices.

Before you have the option to publish, you must configure the [Update Server](updates-publisher-options#update-server) option for Updates Publisher. To open this configuration option, go to **Updates Workspace** &gt; **Overview** and select **Configure WSUS and Signing Certificate.** You can also go to the Update Server page in the Updates Publisher options.

Note

Updates Publisher can only publish updates that are 375 megabytes (MB) or less in size.

### To publish a publication

1. Go to the **Publications Workspace**, and then select a publication that contains the group of updates and bundles that you want to publish or export. Then choose **Publish** from **Home** tab of the ribbon.
2. On the **Select** page of the **Publish** wizard you can choose to sign all updates with a new publishing certificate, but you cannot change the publication type.
3. Complete the wizard.

    If publishing fails, you are presented with a link to the UpdatesPublisher.log file that can provide more information.

## Export a publication

You can export a publication from your Updates Publisher repository. Doing so exports the updates and bundles that are assigned to that publication and creates an update catalog. You can then [add](updates-publisher-catalogs#add-software-update-catalogs) and then [import](updates-publisher-catalogs#import-updates) that catalog to another instance of Updates Publisher. You can also [export updates](manage-updates-with-updates-publisher#export-updates) that are not part of a publication.

To export a publication, go to the **Publications Workspace** and select the publication that contains updates that you want to export. You can only select one publication at a time.

With the publication selected, choose **Export** from the **Home** tab of the ribbon, and then provide a path and filename for the catalog export.

You also have the option to export (include) dependent software updates as part of the export.

## Delete a publication

To delete a publication, select the publication the **Publications Workspace**, and then choose **Delete** from the **Publication** tab of the ribbon.

After the publication is removed from Updates Publisher, the updates that were in the publication remain available in the Updates Publisher repository.

## Expire or reactivate updates and bundles

You can use the **Updates Workspace** to select and then expire or reactivate updates and bundles. You can expire and reactivate updates and bundles as many times as you choose.

- **To expire updates or bundles**, in the Updates Workspace select one or more updates or bundles that are not expired, and then choose **Expire** from the **Home** tab. Until you publish the update or bundle as expired to Configuration Manager, you can reactivate it.

    Before you can remove (delete) a custom update or bundle from Configuration Manager, you must expire it and then publish that expired status to Configuration Manager. After updates or bundles are expired in Configuration Manager, you can no longer deploy or reactivate the update or bundle.
- **To reactivate updates or bundles**, in the Updates Workspace select one or more updates that are expired, and then choose **Reactivate** from the **Home** tab of the ribbon. If the expired update was previously published as expired to Configuration Manager, you cannot reactivate it.