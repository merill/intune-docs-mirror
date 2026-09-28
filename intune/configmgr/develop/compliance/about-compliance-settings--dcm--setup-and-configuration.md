---
layout: Conceptual
title: About Compliance Settings Setup and Configuration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-compliance-settings--dcm--setup-and-configuration
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
description: Learn about how to configure compliance settings and the custom configuration requirements using the Configuration Manager site.
locale: en-us
document_id: fbb42b53-2125-5a5a-5fe3-9217cb2cac0f
document_version_independent_id: 195cf8e8-053e-8140-b2a3-10c8f10e1c7a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/about-compliance-settings--dcm--setup-and-configuration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/about-compliance-settings--dcm--setup-and-configuration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/about-compliance-settings--dcm--setup-and-configuration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 169d9049-86f5-1bd7-55b3-01958e34b013
---

# About Compliance Settings Setup and Configuration - Configuration Manager | Microsoft Learn

To use desired configuration management on your Configuration Manager site, the following needs to be in place:

- The site must be running Configuration Manager.
- Clients must be running the Configuration Manager client.
- The desired configuration management client agent must be enabled.
- Client computers must have installed the .NET Framework 2.0 or a later version.

Enabling the desired configuration management client agent makes it possible for Configuration Manager clients that are assigned to this site to evaluate compliance with assigned configuration baselines. This client agent is enabled by default, but it will not evaluate its compliance until it downloads one or more configuration baselines and evaluates them at the configured schedule.

Disabling the desired configuration client agent prevents Configuration Manager clients that are assigned to this site from evaluating compliance with assigned configuration baselines.

This setting to enable or disable the desired configuration management client agent, together with any assigned configuration baselines, is downloaded to client computers according to the **Policy Polling Interval** in the **Computer Client Agent Properties** dialog box (by default, every 60 minutes).

Note

When the desired configuration management client agent is enabled on client computers, the **Systems Management Properties** dialog box displays a **Configurations** tab that lists the downloaded configuration baselines and the results of its compliance evaluation. When the desired configuration management client agent is disabled, the **Configurations** tab is not visible. If the **Configurations** tab is not visible, the client is not running the desired configuration management client agent. This might be because the site is not enabled for desired configuration management, the client computer has not yet downloaded the policy to enable the desired configuration management client agent, a local policy has disabled the desired configuration management client agent, or the client is not a Configuration Manager client.