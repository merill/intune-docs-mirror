---
layout: Conceptual
title: Prerequisites for power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/prerequisites-for-power-management
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
description: Get the prerequisites for power management in Configuration Manager.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 72109318-20e3-e05e-5bcf-49039a629107
document_version_independent_id: d292c29b-5dc9-add9-59a0-1350245140d4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/power/prerequisites-for-power-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/power/prerequisites-for-power-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/power/prerequisites-for-power-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: 4e3fbbca-b9db-23a9-371e-1ad736e17fba
---

# Prerequisites for power management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Power management in Configuration Manager has external dependencies and dependencies within the product.

## Dependencies external to Configuration Manager

The following table lists the dependencies external to Configuration Manager for using power management.

| Dependency | More information |
| --- | --- |
| Client computers must be able to support the required power states | To use all features of power management, client computers must be able to support the sleep, hibernate, wake from sleep, and wake from hibernate actions. You can use the **Power Capabilities** report to determine if computers can support these actions. For more information, see [Power Capabilities report](monitor-and-plan-for-power-management#BKMK_Capabilites) in the topic [How to monitor and plan for power management](monitor-and-plan-for-power-management). |

## Configuration Manager dependencies

The following table lists the dependencies within Configuration Manager for using power management.

| Dependency | More Information |
| --- | --- |
| Power management must be enabled before you can create and monitor power plans. | For information about how to enable and configure power management, see [Configuring power management](configuring-power-management). |
| Reporting services point | You must configure a reporting services point before you can view power management reports. For more information, see [Introduction to reporting](../../../servers/manage/introduction-to-reporting). |