---
layout: Conceptual
title: Prepare for software updates management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/prepare-for-software-updates-management
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
description: To prepare to manage updates, complete these tasks to display compliance assessment data in the Configuration Manager console.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: ee9d9dfd-2032-f175-2228-d5a90c449aae
document_version_independent_id: 8a9e7f7d-dedd-9cba-0bc4-9f659af35f18
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/get-started/prepare-for-software-updates-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/get-started/prepare-for-software-updates-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/get-started/prepare-for-software-updates-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8acd7587-ec91-2a09-62ef-57cbf860f5c1
---

# Prepare for software updates management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before the compliance assessment data of the software update displays in the Configuration Manager console and before you can deploy software updates to client computers, you must complete the steps in the following sections.

## Step 1: Install a software update point

The software update point is required on the central administration site, or stand-alone primary site, and on primary sites to enable the software updates compliance assessment and to deploy software updates to clients. The software update point is optional on secondary sites. For details, see [Install a software update point](install-a-software-update-point)

## Step 2: Synchronize Software Updates

Software updates synchronization is the process of retrieving the software updates metadata that meets the criteria that you configure. Software updates are not displayed in the Configuration Manager console until you synchronize software updates. For details, see [Synchronize software updates](synchronize-software-updates).

## Step 3: Configure classifications and products to synchronize

Perform this configuration on the central administration site or stand-alone primary site. After you synchronize software updates the first time, Configuration Manager retrieves an updated list of classifications and products. Now, you can select from the new options in the Software Update Point Component properties. After you configure the new classifications and products, repeat step 2 to start software updates synchronization to retrieve software updates metadata for the new criteria. For details, see [Configure classifications and products to synchronize](configure-classifications-and-products).

## Step 4: Manage settings for software updates

After you synchronize software updates, verify Configuration Manager client settings, group policy configurations, and software updates settings before you deploy software updates. For details, see [Manage settings for software updates](manage-settings-for-software-updates).