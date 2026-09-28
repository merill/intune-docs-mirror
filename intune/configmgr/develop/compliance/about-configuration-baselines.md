---
layout: Conceptual
title: About Configuration Baselines - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-configuration-baselines
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
description: In Configuration Manager, baselines are used to define the configuration of a product or a system that is established at a specific point in time, capturing both structure and details.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: a842f745-ac44-5aeb-8d07-93a665d80691
document_version_independent_id: 2536bf3d-ed14-a64f-393b-ca1c89ef0d45
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/about-configuration-baselines.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/about-configuration-baselines
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/about-configuration-baselines.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 3666c89f-1024-e014-3191-19dfa969c709
---

# About Configuration Baselines - Configuration Manager | Microsoft Learn

In Configuration Manager, baselines are used to define the configuration of a product or a system that is established at a specific point in time, capturing both structure and details. Configuration baselines in Configuration Manager contain a defined set of desired configurations that are evaluated for compliance as a group.

Configuration baselines contain one or more configuration items with associated rules, and they are assigned to computers through collections, together with a compliance evaluation schedule.

Note

Although you can assign configuration baselines to a collection that contains users, the configuration baselines will be evaluated only by computers in the collection, and not by users in the collection.

You can create your own configuration baselines with the Configuration Manager console, and you can import configuration baselines from the following sources:

- A Best Practices configuration baseline from Microsoft or other vendors
- Custom authored configuration baselines from within your own organization, but external to Configuration Manager
- Another Configuration Manager site

    When configuration baselines are imported, unless they were originally created in the same Configuration Manager site, you will not be able to directly modify them in the Configuration Manager console. If you need to refine the configuration items to meet your business requirements, the recommended path is:

1. Create child configuration items with your custom values.
2. Duplicate the configuration baseline.
3. Edit the duplicated baseline, and replace the configuration items with your edited child configuration items.

## Configuration Baseline Rules

Configuration baselines rules are used to specify how the configuration items that are included in the configuration baseline are to be assessed for compliance on client computers. There are fixed types of configuration baseline rules that cannot be changed in Configuration Manager. Configuration items can be added to the following configuration baseline rules:

- **One of the following operating system configuration items must be present and properly configured.**
- **These applications and general configuration items are required and must be properly configured.**
- **If these optional application configuration items are detected, they must be properly configured.**
- **These software updates must be present.**
- **These application configuration items must not be present.**
- **These configuration baselines must also be validated.**

### RequiredItems

- These applications and general configuration items are required and must be properly configured.

### ProhibitedItems

- These application configuration items must not be present.

### OptionalItems

- If these optional application configuration items are detected, they must be properly configured.

### OperatingSystems

- One of the following operating system configuration items must be present and properly configured.

### SoftwareUpdates

- These software updates must be present.

### Baselines

- These configuration baselines must also be validated.

### OtherConfigurationItems

- References to content defined as raw Service Modeling Language (SML).