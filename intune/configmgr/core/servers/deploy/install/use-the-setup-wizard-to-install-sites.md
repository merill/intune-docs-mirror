---
layout: Conceptual
title: Setup wizard - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/use-the-setup-wizard-to-install-sites
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
description: Use the Configuration Manager setup wizard to install a new site.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 3a040fe0-162c-1740-9c29-6499a25927b9
document_version_independent_id: a6b16b57-24af-4356-219c-755948beaf01
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/use-the-setup-wizard-to-install-sites
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: 630db2fb-3cd5-08e5-ab2a-2f9c1702676e
---

# Setup wizard - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To install a new Configuration Manager site by using a guided user interface, use the Configuration Manager Setup Wizard (setup.exe). The wizard supports installing a primary site or central administration site (CAS). You also use the wizard to [upgrade an evaluation installation](upgrade-an-evaluation-install-to-a-full-install) of Configuration Manager to a fully licensed installation. When you don't want to use the wizard, you can instead use an [installation script](use-a-command-line-to-install-sites) and run an unattended command-line installation.

Install a secondary site from within the Configuration Manager console. Secondary sites don't support a scripted command-line installation.

Before you install a site, be familiar with the details in the following articles:

- [Design a hierarchy of sites](../../../plan-design/hierarchy/design-a-hierarchy-of-sites)
- [Site and site system prerequisites](../../../plan-design/configs/site-and-site-system-prerequisites)
- [Prepare to install sites](prepare-to-install-sites)
- [Prerequisites for installing sites](prerequisites-for-installing-sites)
- Assess server readiness with the [Prerequisite Checker](prerequisite-checker)
- [Release notes](release-notes)

Tip

If you need assistance with site installation, see the [Support options and community resources](../../../understand/find-help#support-options-and-community-resources). For example, the Microsoft Q&A forum for [Configuration Manager site and client deployment](/en-us/answers/topics/mem-cm-site-deployment.html).

When you're ready to get started, see the following articles for the specific processes:

[Use the setup wizard to install a central administration or primary site](setup-wizard-central-primary)

[Use the setup wizard to install a secondary site](setup-wizard-secondary)