---
layout: Conceptual
title: Evaluate in a lab environment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/evaluate-with-lab-environment
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
description: Create a lab environment to evaluate Configuration Manager for use in your organization.
ms.date: 2017-02-28T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f2711061-e6ed-1a6c-6f5d-c88bebed6ca1
document_version_independent_id: 5a45e0c7-a947-2f9c-c9b2-f012ca2c5a87
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/evaluate-with-lab-environment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/evaluate-with-lab-environment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/evaluate-with-lab-environment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 53a88437-aea4-a972-27f6-61e72050269a
---

# Evaluate in a lab environment - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Learn how to create a lab environment to evaluate Configuration Manager for use in your organization.

Configuration Manager is a complex and powerful tool to manage your users, devices, and software. It's a good idea to thoroughly evaluate Configuration Manager before full deployment, so that you can marry conceptual understanding with hands-on exercises.

This guide is primarily meant for admins who are evaluating the use of Configuration Manager in corporate environments:

- Admins who want a solution to fully manage PCs, servers, and mobile devices
- Admins in high-security industries that require the security of on-premises device management with the flexibility of cloud-based device management
- Admins who want to manage the scaling-up of their on-premises server architecture

## What this lab does

The main goal of creating this lab environment is to give you the general knowledge to start working with Configuration Manager, and to enhance your understanding of Configuration Manager. You'll walk through an expedited assembly of the current version of Configuration Manager, by using two servers:

- One that hosts Active Directory, the domain controller, and the DNS server
- One that hosts Configuration Manager and all associated SQL Server components

Client machines are installed within Hyper-V. The lab itself can also be run as a fully virtualized system on a single server.

## What this lab does not do

This lab will not take you through all Configuration Manager scenarios. It is not designed to be immediately migrated into an active environment.

When you build this lab, you will have a functional environment to work in. But this environment will not be optimized for factors like system performance, hard disk space management, and SQL Server storage.

## Recommended reading before you build the lab

There is a wealth of content available in [Documentation for Configuration Manager](/en-us/sccm/). We recommend that you read the following topics from this library before you start to build the lab:

- Learn core concepts about the Configuration Manager console, end-user portals, and example scenarios in [Introduction to Configuration Manager](../understand/introduction).
- Learn about the primary management capabilities of Configuration Manager in [Features and capabilities of Configuration Manager](../plan-design/changes/features-and-capabilities).
- Bolster your knowledge with [Fundamentals of Configuration Manager](../understand/fundamentals).
- Learn the importance of security roles in [Fundamentals of role-based administration for Configuration Manager](../understand/fundamentals-of-role-based-administration).
- Learn about content management in [Concepts for content management](../plan-design/hierarchy/fundamental-concepts-for-content-management).
- Learn how to successfully support daily tasks throughout your deployment in [Understand how clients find site resources and services for Configuration Manager](../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services).