---
layout: Conceptual
title: Configuration Manager and Windows as a Service - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/configuration-manager-and-windows-as-service
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
description: Get basic information on adopting Configuration Manager current branch to support Windows as a service.
ms.date: 2021-12-07T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 005782d7-c0a4-18ef-9daa-285d6da10f5b
document_version_independent_id: 06baf68c-67a0-6636-c33d-fd871231fc86
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/configuration-manager-and-windows-as-service.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/configuration-manager-and-windows-as-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/configuration-manager-and-windows-as-service.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ddd0a8fb-e570-68a4-64ae-4b9da36d27fe
---

# Configuration Manager and Windows as a Service - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager provides comprehensive control over feature updates for Windows. To fully adopt the Windows as a service model, you also must adopt the Configuration Manager current branch model. To stay current with Windows, requires that you stay current with Configuration Manager for the best experience. New versions of Configuration Manager are required to take full advantage of the exciting new enterprise features for Windows. This article is intended to be a landing page for the key articles required to adopt Configuration Manager current branch. Configuration Manager current branch gets you on your way to Windows as a service.

## Configuration Manager current branch

| Article | Description |
| --- | --- |
| [Overview of Configuration Manager current branch](../plan-design/changes/whats-new-incremental-versions) | Provides a brief summary of the key points for the servicing model for Configuration Manager current branch |
| [Support lifecycle](../servers/manage/current-branch-versions-supported) | Explains the current branch support and servicing model. |
| [Removed and deprecated items](../plan-design/changes/deprecated/removed-and-deprecated) | Provides early notice about future changes that might affect your use of Configuration Manager. |
| [Updates to Configuration Manager current branch](../servers/manage/updates) | Explains the easy in-console method of applying feature updates to Configuration Manager. |
| [Get available updates](../servers/manage/prepare-in-console-updates#get-available-updates) | Explains the two modes available to get new Configuration Manager feature updates. |
| [Update checklist](../servers/manage/prepare-in-console-updates#before-you-install-an-in-console-update) | Provides update version-specific checklists, if applicable. |
| [Install new Configuration Manager feature updates](../servers/manage/install-in-console-updates) | Explains the simple installation steps for feature updates. |
| [Support for Windows 11](../plan-design/configs/support-for-windows-11) | Provides a support matrix for Windows 11 versions. |
| [Support for Windows 10](../plan-design/configs/support-for-windows-10) | Provides a support matrix for Windows 10 versions. |
| [Support for Windows ADK](../plan-design/configs/support-for-windows-adk) | Provides a support matrix for the Windows Assessment and Deployment Kit (Windows ADK). |
| [Technical Previews for Configuration Manager](../get-started/technical-preview) | Provides information about the Configuration Manager technical preview program. |

## Windows as a service

| Article | Description |
| --- | --- |
| [Manage Windows as a service](../../osd/deploy-use/manage-windows-as-a-service) | Explains how to use servicing plans to deploy Windows feature updates. |
| [Upgrade Windows via task sequence](../../osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system) | The details of creating a task sequence to upgrade Windows with additional recommendations. |
| [Phased deployments](../../osd/deploy-use/create-phased-deployment-for-task-sequence) | Phased deployments automate a coordinated, sequenced rollout of a task sequence across multiple collections. |
| [Optimize Windows update delivery](../../sum/deploy-use/optimize-windows-10-update-delivery) | Use Configuration Manager to manage update content to stay current with Windows. |
| [Integrate Windows Update client policies (optional)](../../sum/deploy-use/integrate-windows-update-client-policies) | Explains how to define and deploy Windows Update client policies using Configuration Manager. |
| [Use co-management with Microsoft Intune and Windows Update client policies (optional)](../../comanage/overview) | Provides an overview of co-management. |

## Product lifecycle

Another important aspect of staying current with Windows and Configuration Manager is to monitor product lifecycles. Configuration Manager has built-in features to help:

- Be proactive with dashboards for planning:

    - [Product lifecycle dashboard](../clients/manage/asset-intelligence/product-lifecycle-dashboard): View the Microsoft Lifecycle Policy for applicable products.
    - [Windows servicing dashboard](../../osd/deploy-use/manage-windows-as-a-service): Provides you with information about computers in your environment, servicing plans, and compliance information.
- Be reactive with notifications, management insights, and reports:

    - [Configuration Manager console notifications](../servers/manage/admin-console-notifications#new-notifications-in-version-2010): Look for in-console notifications about devices with operating systems that are past the end of support date and that are no longer eligible to receive security updates.
    - Management insights
        - [Security](../servers/manage/management-insights#security): Identify clients with unsupported antimalware client versions or clients running earlier versions of Windows that don't receive security updates by default.
        - [Simplified management](../servers/manage/management-insights#simplified-management): Identify clients running an unsupported version of Windows or with an earlier version of the Configuration Manager client.
    - Reports:
        - [Data warehouse historical reporting](../servers/manage/list-of-reports#data-warehouse): View computers that are missing software updates.
        - [OS reports](../servers/manage/list-of-reports#operating-system): View computers by OS versions and servicing details.
        - [Software Updates compliance reports](../servers/manage/list-of-reports#software-updates---a-compliance): View software update compliance details.
    - [Power BI sample reports for software updates](../servers/manage/powerbi-sample-reports): Use Power BI to view software update compliance status.