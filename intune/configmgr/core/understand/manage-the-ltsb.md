---
layout: Conceptual
title: Manage the LTSB - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/manage-the-ltsb
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
description: Management differences for the LTSB of Configuration Manager.
ms.date: 2022-03-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 4f9e58c3-01f8-227e-1852-0e0cebba921d
document_version_independent_id: b7b24720-7003-4453-f557-861895ebb1d2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/manage-the-ltsb.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/manage-the-ltsb
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/manage-the-ltsb.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/bba62c59-6b53-4be4-8b9d-6624f9184c22
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/f3a81ffb-ee36-4ec7-b54a-01b6681aff65
platformId: 69715f13-4bce-e39e-dcad-63bdc276c254
---

# Manage the LTSB - Configuration Manager | Microsoft Learn

*Applies to: System Center Configuration Manager (long term servicing branch)*

When you use the long term servicing branch (LTSB) of Configuration Manager, there are important changes that affect how you manage your infrastructure.

The LTSB is generally the same as current branch version 1606, with some exceptions like cloud-attached features. Most tasks you use for planning, deployment, configuration, and day-to-day management are the same.

For example, the LTSB supports the same number of sites, site types, clients, and general infrastructure as the current branch. Use the same guidance for site and hierarchy planning and design as the current branch. Some features are supported by both branches, like software updates or OS deployment. Use the same guidance as the current branch, with the understanding that there were feature changes since version 1606 of the current branch.

The following sections provide information about tasks that aren't similar between the long term servicing branch and the current branch.

## Updates and servicing

Only critical security updates are made available as in-console updates in the LTSB.

Regular updates for the current branch are visible in the console, but aren't made available to the LTSB. They aren't downloaded and can't be installed.

To support in-console updates for critical security fixes, an LTSB site requires the use of the [service connection point](../servers/deploy/configure/about-the-service-connection-point). You can configure this site system role in offline or online mode, the same as for the current branch. The LTSB collects and submits the same diagnostic and usage data as the current branch.

The LTSB supports the use of the hotfix installer and the update registration tool, as documented for the current branch.

For general information about updates and servicing, see [Updates for Configuration Manager](../servers/manage/updates).

## Changes for site expansion and the `CD.Latest` folder

When you use the LTSB, and expand a stand-alone primary site with a new central administration site (CAS), run setup and the source files from the version 1606 baseline media. For the current branch, you run setup and use source files from the `CD.Latest` folder.

Although you don't run setup for site expansion from the `CD.Latest` folder, continue to use the `CD.Latest` folder for the following actions:

- Site recovery
- Install a new child primary site when your first LTSB site was a CAS

For more information about site expansion, see [Expand a stand-alone primary site](../servers/deploy/install/setup-wizard-central-primary#expand-a-stand-alone-primary-site). For more information about the `CD.Latest` folder, see [The `CD.Latest` folder](../servers/manage/the-cd.latest-folder).

## Recovery

When you recover a site, you must restore the site or site database to its original branch. You can't recover a current branch site database to an LTSB installation, or an LTSB site to a current branch installation.