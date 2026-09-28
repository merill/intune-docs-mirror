---
layout: Conceptual
title: Setup reference - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/setup-reference
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
description: Review this reference to help you prepare to install a Configuration Manager site or hierarchy.
ms.date: 2022-01-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 14b63c0d-d45f-a976-a527-f73ea8d3671b
document_version_independent_id: 0504ebc8-c781-1c69-cb1d-e1b44e3a9156
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/setup-reference.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/setup-reference
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/setup-reference.md
cmProducts: []
platformId: a4ded123-9004-86eb-8ab7-be2643450883
---

# Setup reference - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager Setup provides links to several topics that are detailed in the following sections. The information presented here can help you prepare to install a Configuration Manager site or hierarchy, and help prepare you for some of the decisions you must make during the installation.

## Before you begin

Before you install new Configuration Manager sites, make sure you have reviewed the following information, which can help set the stage for a successful deployment design:

- [Fundamentals of Configuration Manager](../../../understand/fundamentals)
- [Plan for Configuration Manager infrastructure](../../../plan-design/network/configure-firewalls-ports-domains)
- [Prepare to install Configuration Manager sites](prepare-to-install-sites)

## Assess server readiness

Before you begin the installation of a new site, make sure that the site server and the remote site system servers you plan to use for the site (for example, the server that hosts the site database) meet all prerequisite configurations. These topics in the documentation library can help:

- [Supported configurations for Configuration Manager](../../../plan-design/configs/supported-configurations)
- [Prerequisite Checker](prerequisite-checker)

## Usage data levels and settings

When you install your first Configuration Manager site, Configuration Manager automatically installs and configures a new site system role, the **service connection point**, on the site server. The service connection point has these default settings:

- **Online** mode (an offline mode also is available)
- **Enhanced** data collection level (two other data collection levels, Basic and Full, also are available)

When the service connection point site system role is online, Microsoft can automatically collect diagnostics and usage information over the Internet. Information that is collected helps us:

- Identify and troubleshoot problems
- Improve our products and service
- Identify updates for Configuration Manager that apply to the version of Configuration Manager you use

### Levels of data collection

Data collection includes these three levels:

- **Basic** includes data about setup and upgrade, like the number of sites and which Configuration Manager features are enabled. No personally identifiable information is transmitted.
- **Enhanced** includes the data in the Basic level setting, plus it transmits data about the hierarchy, how each feature is used (frequency and duration), and enhanced diagnostic information like the memory state of your server when a system or app crash occurs. No personally identifiable data is transmitted.
- **Full** includes the data in the Basic and Enhanced level settings, and it also sends advanced diagnostic information like system files and memory snapshots. This option might include personally identifiable information, but we won't use that information to identify or contact you, or to target advertising to you.

For more information, including disclosure of the details collected by each level, see [Diagnostics and usage data for Configuration Manager](../../../plan-design/diagnostics/diagnostics-and-usage-data).

For more information, see the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).