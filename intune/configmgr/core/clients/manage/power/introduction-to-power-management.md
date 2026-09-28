---
layout: Conceptual
title: Introduction to power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/introduction-to-power-management
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
description: Get an introduction to power management in Configuration Manager.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 81304a4a-1d2e-7889-530d-ac859cc0df9c
document_version_independent_id: b5e53d09-5d04-d61b-e45d-49a10aabd1a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/power/introduction-to-power-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/power/introduction-to-power-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/power/introduction-to-power-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e7e51a2-3d3c-dfb3-2ba2-d3aa9e0d0c03
---

# Introduction to power management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Power Management in Configuration Manager addresses the need that many organizations have to monitor and reduce the power consumption of their computers. The feature takes advantage of the power management features built into Windows to apply relevant and consistent settings to computers in the organization. You can apply different power settings to computers during business hours and nonbusiness hours. For example, you might want to apply a more restrictive power plan to computers during nonbusiness hours. In cases where computers must always remain turned on, you can prevent power management settings from being applied.

Power management in Configuration Manager includes several reports to help you analyze power consumption and computer power settings in your organization. You can also use the reports to help you troubleshoot problems with power management.

For a detailed workflow about how to configure and use power management, see [Administrator checklist for power management](administrator-checklist-for-power-management).

Important

Configuration Manager power management is not supported on virtual machines. You cannot apply power plans to virtual machines, nor can you or report power data from them.

## The power management workflow

Use the following three phases to plan and implement power management in Configuration Manager.

### Monitoring and planning phase

Power Management uses Configuration Manager hardware inventory to collect data about computer usage and power settings for computers in the site. There are a number of reports that you can use to analyze this data and determine the optimal power management settings for computers. For example, during the monitoring and planning phase of the power management workflow, you can create collections that are based on the data that is included in the **Power Capabilities** report and use that data to identify the computers that are not capable of power management. Then, you can exclude those computers from power management.

Important

Do not apply power plans to computers in your site until you collect and analyze the power data from client computers. If you apply new power management settings to computers without first examining the existing settings, you might experience an increase in power consumption.

### Enforcement phase

Power management lets you create power plans that you can apply to collections of computers in your site. These power plans configure Windows power management settings on computers. You can use the power plans that are included with Configuration Manager, or you can configure your own custom power plans. You can use the power data that is collected during the monitoring and planning phase as a baseline to help you evaluate power savings after you apply a power plan to computers. For more information, see [Administrator checklist for power management](administrator-checklist-for-power-management).

### Compliance phase

In the compliance phase, you can run reports that help you to evaluate power usage and power cost savings in your organization. You can also run reports that describe the improvements in the amount of CO2 generated by computers. Reports are also available that help you validate that power settings were correctly applied to computers and that help you troubleshoot problems with the power management feature.