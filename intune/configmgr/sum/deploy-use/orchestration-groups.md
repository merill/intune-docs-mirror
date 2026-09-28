---
layout: Conceptual
title: Orchestration groups - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/orchestration-groups
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
description: About orchestration groups and their prerequisites and limitations.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 9c5f0d89-c8f6-19a5-70b1-03b590fa59ee
document_version_independent_id: 2202ffcd-6bcf-454c-11ae-f62b31ac31e2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/orchestration-groups.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/orchestration-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/orchestration-groups.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 02758777-91b9-72d0-da71-193fe34e644d
---

# Orchestration groups - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Create an orchestration group to better control the deployment of software updates to devices. Many server administrators need to carefully manage updates for specific workloads, and automate behaviors in between.

[![Screenshot of the Scripts tab in the Orchestration Group node.](media/9957939-orchestration-group-scripts-tab.png)](media/9957939-orchestration-group-scripts-tab.png#lightbox)

An orchestration group gives you the flexibility to update devices based on a percentage, a specific number, or an explicit order. You can also run a PowerShell script before and after the devices run the update deployment.

Members of an orchestration group can be any Configuration Manager client, not just servers. The orchestration group rules apply to the devices for all software update deployments to any collection that contains an orchestration group member. Other deployment behaviors still apply. For example, maintenance windows and deployment schedules.

Note

Starting in Configuration Manager version 2111, Orchestration groups is no longer a pre-release feature. For more information, see [Pre-release features](../../core/servers/manage/pre-release-features).

The **Orchestration Groups** feature is the evolution of the [Server Groups](service-a-server-group) feature. An orchestration group is an object in Configuration Manager.

## Orchestration group usage example

- As the software updates administrator, you manage all updates for your organization.
- You have one large collection for all servers and one large collection for all clients. You deploy all updates to these collections.
- The SQL Server administrators want to control all the software installed on the SQL Servers. They want to patch five servers in a specific order. Their current process is to manually stop specific services before installing updates, and then restart the services afterwards.
- You create an orchestration group and add all five SQL Servers. You also add pre- and post-scripts, using the PowerShell scripts provided by the SQL Server administrators.
- During the next update cycle, you create and deploy the software updates as normal to the large collection of servers. The SQL Server administrators run the deployment, and the orchestration group automates the order and services.

## Prerequisites

### Site server and permission prerequisites

- To see all of the orchestration groups and updates for those groups, your account needs to be a **Full Administrator**.
    - Role-based administration for orchestration groups currently isn't available.
- Enable the **Orchestration Groups** feature. For more information, see [Enable optional features](../../core/servers/manage/optional-features).
    - When you enable **Orchestration Groups**, the site disables the **Server Groups** feature. This behavior avoids any conflicts between the two features.

### Client prerequisites

- Upgrade the target devices to the latest version of the Configuration Manager client.
- Members of an orchestration group should be assigned to the same site.
- Devices can't be in more than one orchestration group.
    - Devices already in an orchestration group won't be available to select when adding new members.

### Permissions for approving scripts

*(Introduced in version 2111)*

Approving scripts for orchestration groups requires one of the following security roles:

- Full Administrator
- Operations Administrator

## Limitations

- You can have up to 1000 orchestration group members.
- Orchestration groups don't work in interoperability mode. For more information, see [Interoperability between different versions of Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions#limitations-in-a-mixed-version-hierarchy).
- If updates are initiated by users from Software Center, orchestration will be bypassed.
- Starting in Configuration Manager version 2103, updates in the **Definition**[classification](../get-started/configure-classifications-and-products) don't require orchestration and will always bypass orchestration group rules.
- Scripts that have parameters aren't supported

## Server groups are automatically updated to orchestration groups

The **Orchestration Groups** feature is the evolution of the [Server Groups](service-a-server-group) feature. When you install Configuration Manager version 2002 or later and you have Server Groups enabled, your server groups are automatically moved to orchestration groups.