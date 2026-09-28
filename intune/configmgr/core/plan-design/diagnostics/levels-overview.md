---
layout: Conceptual
title: Levels of diagnostic usage data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/levels-overview
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
description: Learn about the levels of diagnostics and usage data that Configuration Manager collects
ms.date: 2026-08-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 294338bf-d704-1705-a689-e55a70257d8f
document_version_independent_id: a7d723de-41be-5f0f-2dec-25519b8dbe30
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/levels-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/levels-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/levels-overview.md
cmProducts: []
platformId: d474c2d3-8703-ca23-b05f-7d381ef0ffe4
---

# Levels of diagnostic usage data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager collects three levels of diagnostics and usage data: **Basic**, **Enhanced**, and **Full**. By default, this feature is set at the Enhanced level.

Important

Configuration Manager doesn't collect site codes, sites names, IP addresses, user names, computer names, physical addresses, or email addresses on the Basic or Enhanced levels. Any collection of this information on the Full level isn't purposeful. It's potentially included in advanced diagnostic information like log files or memory snapshots. Microsoft doesn't use this information to identify you, contact you, or develop advertising.

## Levels

### Basic

The Basic level includes data about your hierarchy. It's required to help improve your installation or upgrade experience. This data also helps determine the Configuration Manager updates that are applicable for your hierarchy.

### Enhanced

The Enhanced level is the default after setup finishes. This level includes data that's collected in the Basic level and feature-specific data. It shows frequency and duration of use of different features. It also includes Configuration Manager client settings data: component name, state, and certain settings like polling intervals. Information about software updates is basic on feature usage, it doesn't include data about update compliance at this level.

Microsoft recommends this level because it provides the minimum data to make product and service improvements.

Some examples of data that this level doesn't collect include:

- Names of sites, users, computer, or other objects
- Details of security-related objects
- Vulnerabilities like counts of systems that require software updates

### Full

The Full level includes all data in the Basic and Enhanced levels. It also includes additional information about Endpoint Protection, update compliance percentages, and software update information. This level can also include advanced diagnostic information like system files and memory snapshots. This advanced data might include personal information exists in memory or log files at the time of capture.

## How to change the level

To change the data collection level, you need **Modify** permissions on the **Site** object class.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. Select **Hierarchy Settings** in the ribbon.
3. Switch to the **Diagnostic and Usage Data** tab, then choose the data level.

## Data collected for supported current branch versions

The diagnostic and usage data collected at each level is consistent across supported current branch versions. For the complete list, see [Diagnostic and usage data for supported current branch versions](levels-of-diagnostic-usage-data-collection).

For a list of the currently supported releases, see [Support for Configuration Manager current branch versions](../../servers/manage/current-branch-versions-supported).