---
layout: Conceptual
title: Software updates in the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/software-updates
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
description: Software updates for Configuration Manager devices from the admin center
ms.date: 2022-06-07T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: bf151c9c-f262-a9ad-918a-9fee3fbd964b
document_version_independent_id: bf151c9c-f262-a9ad-918a-9fee3fbd964b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/software-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/software-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/software-updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 9932c4f6-3696-73b9-4aa8-27a998faad82
---

# Software updates in the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The **Software updates** page in the admin center displays the status of software updates status for devices. You can review updates that have successfully installed, failed, or that are assigned but not yet installed. Using the timestamp for the update status assists with troubleshooting.

Important

The **Software updates** page shows status of software updates managed by Configuration Manager only. If the device is also co-managed and the Windows Update workload is managed by Intune, then the blade does not show the status of the software updates managed by Intune.

## Software updates page overview

Each tenant attached device lists its applicable updates and the status of each update on the **Software updates** page. The **Software updates** page is populated with data from Configuration Manager software update scans.

[![This screenshot displays software updates page for a device.](media/13035723-software-updates-page.png)](media/13035723-software-updates-page.png#lightbox)

## Prerequisites

- All of the prerequisites for [Tenant attach: ConfigMgr client details](client-details).
- A minimum of Configuration Manager version 2111 with [update rollup KB12896009](../hotfix/2111/12896009) installed on all sites in the hierarchy.

## Display the Software updates page

To display the **Software updates** page for a device, use the following steps:

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **Software updates**.

## Update details

Selecting an update from the **Software updates** page opens the details pane for the update. The details pane lists the title of the update along with its description, classification, product category, and link to technical information about the specific update. The pane also includes the status and the status time for the selected update on the selected device.

[![ Screenshot displaying the details pane for an update.](media/13035723-software-updates-details.png)](media/13035723-software-updates-details.png#lightbox)

### Software updates page options

**Searching:** Searching is enabled for every category except for **Status time**. You can search for a string of words, a single word, or a partial word. For instance, searching for the string `compliant` would display results that contain the string `compliant` that would include `non-compliant`.

[![This screenshot shows searching a feature on software updates page.](media/13035723-software-updates-filter.png)](media/13035723-software-updates-filter.png#lightbox)

**Sorting:** You can sort by any column. The default view is sorted based on the **Status time**.

**Refresh:** You can refresh to display the latest information from the on-premises server at any time.

**Paging & Caching:** Paging is fully implemented with each page having a maximum of 25 software update entries. Each time you select **Next**, the data is retrieved from the on-premises server. Once the data is retrieved the first time, it's cached for the browser to allow for quick page loading.

**Filters:** You can filter the available software updates based on their **Status** values, **Classification** values, or both values.

**Export:** Allows you to export all your available data, across all pages, while honoring any applied search teams and filters. The data is exported to a `.csv` file.

## Update status values

The following **Status** values are used in the **Software updates** page:

- **Unknown**: The status of the update isn't known or is currently unavailable.
- **Compliant**: The update is fully compliant and assigned.
- **Non-compliant**: The update isn't compliant (this message doesn't mean there was an error though), it just means it's either an older version or unapproved.
- **Conflict detected**: There's some sort of conflict with other software on the machine causing the update to fail.
- **Error**: The update failed with an error.
- **Partial compliance**: The update is installed and partially compliant. That is, part of the software update isn't compliant.