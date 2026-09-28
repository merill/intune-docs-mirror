---
layout: Conceptual
title: Collection Evaluation Viewer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/ceviewer
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
description: Use the Collection Evaluation Viewer to view and troubleshoot the collection evaluation process in Configuration Manager.
ms.date: 2021-04-27T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 28e7af11-76d5-355f-c4a7-86ac19332150
document_version_independent_id: 74fd3c4e-4b64-55b9-110f-3d2d1b286b3f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/ceviewer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/ceviewer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/ceviewer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 6c80d8b7-cebf-9875-2517-04ffa9e7fc01
---

# Collection Evaluation Viewer - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Collection Evaluation Viewer is one of the [Configuration Manager tools](tools). Use it to view and troubleshoot the collection evaluation process on the primary site server.

Important

Starting in Configuration Manager version 2103, this standalone tool isn't supported. The tool is no longer included with the Configuration Manager installation source. Starting in version 2010, its functionality is built-in to the console. For more information, see, [How to view collection evaluation](../clients/manage/collections/collection-evaluation-view).

The tool displays the following information:

- Both historic and live information for full and incremental collection evaluations
- The evaluation queue status
- The time for collection evaluations to complete
- Which collections are currently being evaluated
- The estimated time that a collection evaluation will start and complete

## About collection evaluation

The collection evaluation process runs by evaluating the membership rules of a collection to update its members. The site places a collection that it's evaluating in one of four different queues:

- **Manual Queue**: For collections that an administrator has manually selected for evaluation from the console
- **New Queue**: For newly created collections
- **Full Queue**: For collections due for full evaluation
- **Incremental Queue**: For collections with incremental evaluation

There are four threads that run to evaluate the collections in the above queues. Each queue includes a series of arrays, and each array includes the collections to be evaluated. The thread that's running for the queue selects a collection from the array and runs the evaluation. The queue length indicates the number of arrays in the queue.

## Requirements

- Run the tool on the site server
- Run the tool by an administrative user with at least the **Read-Only Analyst** role
- The user also requires **Read** permission to the site database in SQL
- SQL must be on the default port

## Usage

Run **CEViewer.exe**. The main menu of the tool contains the following tabs:

- Connect: Establish the initial connection to the primary site server and SQL Server
- Full Evaluation: Lists the detailed information about all past full evaluations
- Incremental evaluation: Lists the detailed information about all past incremental evaluations
- All Queues: Summarizes the current collection evaluations for all four queues
- Manual Queue: Lists the detailed information about the current collection evaluation in the manual queue
- New Queue: Lists the detailed information about the current collection evaluation in the new queue
- Full Queue: Lists the detailed information about the current collection evaluation in the full queue
- Incremental Queue: Lists the detailed information about the current collection evaluation in the incremental queue

### Connect tab

This tab allows you to establish the initial connection to the primary site server. The tool also establishes a connection to the SQL Server that hosts the site database.

The connections to both primary site server and SQL Servers use the current signed-in user credential. Connections to the central administration site or a secondary site aren't supported. No collection evaluation process runs on those sites.

Once the tool successfully establishes a connection, see a notification at the bottom of the Collection Evaluation Viewer that confirms the tool's connection to the SQL Server.

### Full Evaluation tab

Shows detailed information about past full collection evaluations. There are eight columns:

- **Collection Name**: Name of the collection
- **Site ID**: Site ID of the collection
- **Run Time**: How long the last collection evaluation ran, in seconds
- **Last Evaluation Completion Time**: When the last collection evaluation completed
- **Next Evaluation Time**: When the next full evaluation starts
- **Member Changes**: The member changes in the last collection evaluation. These changes are either plus (members added) or minus (members removed).
- **Last Member Change Time**: The most recent time that there was a membership change in the collection evaluation
- **Percent**: The percentage of evaluation time for this collection over the total (all collections) evaluation time

### Incremental evaluation tab

Shows detailed information about past incremental collection evaluations. There are seven columns:

- **Collection Name**: Name of the collection
- **Site ID**: Site ID of the collection
- **Run Time**: How long the last collection evaluation ran, in seconds
- **Last Evaluation Completion Time**: When the last collection evaluation completed
- **Member Changes**: The member changes in the last collection evaluation. These changes are either plus (members added) or minus (members removed).
- **Last Member Change Time**: The most recent time that there was a membership change in the collection evaluation
- **Percent**: The percentage of evaluation time for this collection over the total (all collections) evaluation time

### All Queues tab

Summarizes the live collection evaluations for all four queues. There are six sections:

- **Summary**: Lists the total collection number and the queue length for all collections in all four queues
- **Running Evaluation**: Lists which collection is currently being evaluated in each queue, and how long it has been running
- **Manual Update**: Shows a brief summary of the collections being evaluated, the estimated completion time, and the order of the evaluation in the manual queue
- **New Collection**: Shows a brief summary of the collections being evaluated, the estimated completion time, and the order of the evaluation in the new collection queue
- **Full Evaluation**: Shows a brief summary of the collections being evaluated, the estimated completion time, and the order of the evaluation in the full evaluation queue
- **Incremental Evaluation**: Shows a brief summary of the collections being evaluated, the estimated completion time, and the order of the evaluation in the incremental evaluation queue

### Manual Queue tab

Shows information about the manual collection evaluation currently being evaluated. The order in the list is the order in which the collection will be evaluated. There are four columns:

- **Collection Name**: Name of the collection
- **Site ID**: Site ID of the collection
- **Estimated Completion Time**: When the evaluation is estimated to complete
- **Estimated Run Time**: How long the evaluation is estimated to run, in day:hour:minute:second format

### New Queue tab

Shows the live information about the new collection evaluation being evaluated. The order in the list is the order in which the collection will be evaluated. There are four columns:

- **Collection Name**: Name of the collection
- **Site ID**: Site ID of the collection
- **Estimated Completion Time**: When the evaluation is estimated to complete
- **Estimated Run Time**: How long the evaluation is estimated to run, in day:hour:minute:second format

### Full Queue tab

Shows information about the full collection evaluation currently being evaluated. The order in the list is the order in which the collection will be evaluated. There are four columns:

- **Collection Name**: Name of the collection
- **Site ID**: Site ID of the collection
- **Estimated Completion Time**: When the evaluation is estimated to complete
- **Estimated Run Time**: How long the evaluation is estimated to run, in day:hour:minute:second format

### Incremental Queue tab

Shows information about the incremental collection evaluation currently being evaluated. The order in the list is the order in which the collection will be evaluated. There are four columns:

- **Collection Name**: Name of the collection
- **Site ID**: Site ID of the collection
- **Estimated Completion Time**: When the evaluation is estimated to complete
- **Estimated Run Time**: How long the evaluation is estimated to run, in day:hour:minute:second format