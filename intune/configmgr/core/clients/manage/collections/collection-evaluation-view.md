---
layout: Conceptual
title: How to view collection evaluation - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/collection-evaluation-view
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
description: View collection evaluation queues and evaluation-related information.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 1cfa243a-c916-bb98-bc21-f29b13766c87
document_version_independent_id: 192349d2-5951-1fd8-5481-4271e71d4455
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/collections/collection-evaluation-view.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/collections/collection-evaluation-view
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/collections/collection-evaluation-view.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: fedef733-632b-9050-d8eb-8b9b5443bd0e
---

# How to view collection evaluation - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in Configuration Manager version 2010, the functionality of [Collection Evaluation Viewer](../../../support/ceviewer) is integrated into the Configuration Manager console. On each **primary site**, this functionality provides administrators a central location to view and troubleshoot the [collection evaluation](collection-evaluation) process. The console displays the following information:

- Historic and live information for full and incremental collection evaluations
- The evaluation queue status
- The time for collection evaluations to complete
- Which collections are currently being evaluated
- The estimated time that a collection evaluation will start and complete

Tip

Viewing collection evaluation at the CAS changed in Configuration Manager version 2103. For more information, see the Collection evaluation information at the CAS section.

When using the console connected to a CAS using Configuration Manager 2010, you'll see the following behavior:

- Evaluation-related columns for device collections won't contain data.
- The **Collection Evaluation** node under the **Monitoring** workspace isn't shown.
- Evaluation-related information, such as evaluation status and links to the collection evaluation queues, won't be shown in the collection **Summary** group pane.

## Collection evaluation queues

The collection evaluation process evaluates the membership rules of a collection to update its members. A primary site places a collection that it's evaluating into one of four different queues:

- **Full Evaluation Queue**: For collections due for full evaluation
- **Incremental Evaluation Queue**: For collections with incremental evaluation
- **Manual Evaluation Queue**: For collections that an administrator has manually selected for evaluation from the console
- **New Evaluation Queue**: For newly created collections

## Add columns for the Device Collections node

Adding columns to the **Device Collections** node allows you to view collection evaluation information for multiple collections.

1. Connect the Configuration Manager console to a primary site.
2. Go to **Assets and Compliance** &gt; **Overview** &gt; **Device Collections**.
3. Add any or all of the following columns prefixed by the type of evaluation:
    - **Evaluation (Full)**
        - **Last Completion Time**: When the last collection evaluation completed (default column)
        - **Run Time**: How long the last collection evaluation ran, in seconds
        - **Next Refresh Time**: When the next full evaluation starts
        - **Member Changes**: The member changes in the last collection evaluation. Positive numbers mean members were added while negative numbers mean members were removed.
        - **Last Member Change Time**: The most recent time that there was a membership change in the collection evaluation
    - **Evaluation (Incremental)**
        - **Last Evaluation Completion Time**: When the last collection evaluation completed
        - **Run Time**: How long the last collection evaluation ran, in seconds
        - **Member Changes**: The member changes in the last collection evaluation. These changes are either plus (members added) or minus (members removed).
        - **Last Member Change Time**: The most recent time that there was a membership change in the collection evaluation

[![Evaluation-related information columns for the collections node](media/6251274-add-collection-evaluation-columns.png)](media/6251274-add-collection-evaluation-columns.png#lightbox)

## View evaluation information from the collection summary

View the collection summary information to get information specific to the evaluation of a single collection.

1. Connect the Configuration Manager console to a primary site.
2. Go to **Assets and Compliance** &gt; **Overview** &gt; **Device Collections**.
3. Select a collection from the **Device Collections** node.
4. In the **Summary** group pane for collection, review the evaluation-related information for the selected collection. [![Evaluation-related information in the summary group for the selected collection](media/6251274-summary-collection-evaluation.png)](media/6251274-summary-collection-evaluation.png#lightbox)
5. The **Related Objects** give links to view status of the collection in the specific queue. These links take you to the queues in the **Monitoring** workspace under the **Collection Evaluation**node.
    - This action creates a new node is created where you can see the evaluation status for the specific collection.

## Monitoring collection evaluation queues

Monitoring the collection evaluation queues can give you deeper insight into the collection evaluation process.

1. Connect the Configuration Manager console to a primary site.
2. From the **Monitoring** workspace, go to the **Collection Evaluation** node. Starting in Configuration Manager 2103, go to **Monitoring** &gt; **Collection Evaluation** &gt; **Collection Evaluation Queue**.The following queues are summarized and have their own nodes:
    - **Full Evaluation Queue**: For collections due for full evaluation
    - **Incremental Evaluation Queue**: For collections with incremental evaluation
    - **Manual Evaluation Queue**: For collections that an administrator has manually selected for evaluation from the console
    - **New Evaluation Queue**: For newly created collections
3. The total number of collections in queue and queue length is listed as a summary. Additionally, the following status summaries for the evaluation queues are listed:
    - Number of collections in queue
    - Queue length
    - Current evaluation collection
    - Current evaluation started on
    - Current evaluation elapsed (seconds)
4. Starting in Configuration Manager 2103, you can: 
    - Configure a primary site's refresh interval for the **Collection Evaluation** statistics page to be between 1 minute and 1440 minutes (1 day). Typically, collection evaluation occurs over the course of seconds or minutes. However, you can change the statistics refresh to accommodate your environment. The default **Refresh Interval (minutes)** is 5.
    - Copy collection evaluation statistics as structured text to the clipboard. Use the **Copy** button in the ribbon to copy the statistics. When the text is pasted into a text editor, it's structured to make it easy to read.
5. Selecting the node for a queue brings up detailed status for the queue including:
    - **Name**: Name of the collection
    - **Collection ID**: ID of the collection
    - **Estimated Completion Time**: When the evaluation is estimated to complete
    - **Estimated Run Time**: How long the evaluation is estimated to run, in day:hour:minute:second format

[![Manual Evaluation Queue node containing detailed information about collection evaluation](media/6251274-manual-evaluation-queue.png)](media/6251274-manual-evaluation-queue.png#lightbox)

## Full and incremental evaluation status nodes

*(Introduced in 2103)*

The **Full Evaluation Status** and **Incremental Evaluation Status** subnodes have been added to the **Collection Evaluation** node in the **Monitoring** workspace.

- On a primary site, **Full Evaluation Status** and **Incremental Evaluation Status** show the data for the local evaluations.
- On a CAS, **Full Evaluation Status** and **Incremental Evaluation Status** shows the data from the primary site with the longest run time.

    - Using the longest runtime for these nodes is the same logic that's used for the collection evaluation columns at the CAS.

[![Full Evaluation Status node at the CAS ](media/8787410-full-evaluation-status-node-cas.png)](media/8787410-full-evaluation-status-node-cas.png#lightbox)

## Collection evaluation information at the CAS

*(Introduced in 2103)*

Since collection evaluation happens at the primary site level, the collection evaluation view on the CAS is a summary of what's occurring on the primary sites. Starting in Configuration Manager version 2103, there are two new tabs in the details pane of the collection view in the console. The following new tabs show collection evaluation information from all primary sites in hierarchy:

- **Evaluation (Full) In Hierarchy**
- **Evaluation (Incremental) In Hierarchy**

[![Collection evaluation tabs in the collection's details pane at the CAS](media/8787410-collection-evaluation-details-tab.png)](media/8787410-collection-evaluation-details-tab.png#lightbox)

From the **Device Collections** node at the CAS, the evaluation columns display the evaluation status from the primary site with the longest run time. The column information at the CAS for the full evaluation status could be from a different primary site than the incremental information since the longest runtime for the incremental might have occurred at a different primary.

For instance, incremental evaluation for the `All Systems` collection on the `WMI` primary site takes longer than the other primary sites. The full evaluation columns on the CAS display the information from primary site `WMI` for the `All Systems` collection in the **Device Collections** node.

[![Collection evaluation columns at the CAS with the details tab open displaying the evaluation from all primary sites](media/8787410-cas-collection-evaluation-columns.png)](media/8787410-cas-collection-evaluation-columns.png#lightbox)

## Drill through from collection evaluation queue or status view to a collection

*(Introduced in 2103)*

You can navigate to a collection in the **Assets and Compliance** workspace from a collection evaluation status view or evaluation queue in the **Monitoring** workspace. Select a collection from one of the status views or queues, then choose **View collection** from the ribbon or right-click menu to open the collection.

Navigation to the collection from queues won't occur if the collection evaluation has completed. You can only drill though from an item in a queue that's still currently running its evaluation. If the evaluation has already completed, the **View collection** action takes you to the main collection view. Drill though from the evaluation status views, **Full Evaluation Status** and **Incremental Evaluation Status**, will always take you to the collection.

[![View collection option in the ribbon of the Full Evaluation Status node](media/8787410-view-collection.png)](media/8787410-view-collection.png#lightbox)