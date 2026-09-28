---
layout: Conceptual
title: Author configuration baselines and items - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-authoring-configuration-baselines-and-configuration-items
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
ms.date: 2019-08-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
description: Learn about how to configure data through the Configuration Manager console or directly editing the DCM Digest XML file.
locale: en-us
document_id: 26d7fbdd-557e-da7b-6c3b-7effdb62a741
document_version_independent_id: 2aacb626-9f1d-1d9e-1e9e-b52eaaab6fe7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/about-authoring-configuration-baselines-and-configuration-items.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/about-authoring-configuration-baselines-and-configuration-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/about-authoring-configuration-baselines-and-configuration-items.md
cmProducts: []
platformId: 79c005b4-543e-3d49-7f97-cefd90732e3a
---

# Author configuration baselines and items - Configuration Manager | Microsoft Learn

Configuration Manager supports the authoring of configuration data, which consists of configuration baselines and configuration items. Configuration Manager presents this configuration data in a user-friendly format called DCM Digest. This format is a specialized XML document that Configuration Manager uses. You can author configuration data by using the Configuration Manager console, or by directly authoring a DCM Digest XML file.

When you create configuration data with the Configuration Manager console, you can export it into a .cab file. When configuration data is imported into Configuration Manager, the format is DCM Digest XML only.

## Authoring configuration data

Create configuration data in the following ways:

- You can create configuration data externally with an XML editor. If you then package it as a .cab file, you can import it into Configuration Manager.
- You can create configuration data within Configuration Manager by using the following wizards:

    - Create Application Configuration Item Wizard
    - Create Operating System Configuration Item Wizard
    - Create Configuration Baseline

Important

You create and manage software update configuration items through the software updates management feature in Configuration Manager. You can reference these configuration items by configuration baselines. However, don't directly author them by using configuration items or the DCM Digest.

You can also import configuration data that software vendors and solution providers have published.

Note

You can digitally sign published configuration data. Then you can verify the publishing source and be sure that no one has tampered with the data. If the digital signature verification check fails, Configuration Manager warns you to continue with the import. Only import configuration data from external sources if it has a valid digital signature from a trusted publisher.

After the site imports the configuration data, you can then work with it in the Configuration Manager console.