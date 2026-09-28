---
layout: Conceptual
title: Installation scenarios - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/scenarios-to-streamline-your-installation
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
description: Learn techniques for installing a new Configuration Manager hierarchy when you update or upgrade a site.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d9796c85-c313-98b4-d753-4ff64e144e7c
document_version_independent_id: c99b3b75-26ef-57ed-b7cb-0d04a54014ca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/scenarios-to-streamline-your-installation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/scenarios-to-streamline-your-installation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/scenarios-to-streamline-your-installation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: 112d4c92-3537-596f-3164-c3bf57b11587
---

# Installation scenarios - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

With the release of update versions for Configuration Manager current branch, there are new scenarios to streamline the install of a new hierarchy to an update version. You can also use these techniques to upgrade from Microsoft System Center 2012 Configuration Manager.

The following list is a summary of the two main scenarios:

- Install a new Configuration Manager current branch hierarchy that runs an update version.

    - Install only the top-tier site with a baseline version. Then immediately install an update to bring that site current with the update version that you'll use. Then install others sites directly to that update version.
    - This process skips the installation of other sites to a baseline level, and then updating them to the update version that you want to use.
    - The process also skips the installation of clients to a baseline version, and then reinstalling them when you update to a later version.
- Upgrade a Microsoft System Center 2012 Configuration Manager infrastructure to an update version of Configuration Manager.

    - Manually upgrade your central administration site (CAS) and each primary site to a baseline version before you install an update version.
    - Don't upgrade secondary sites from Microsoft System Center 2012 Configuration Manager until your primary sites run the update version that you'll use.
    - Don't upgrade clients from Microsoft System Center 2012 Configuration Manager until your primary sites run the update version that you'll use.

## Install a new hierarchy to an update version

1. Install a top-level site for your new hierarchy by using the baseline media. You can use baseline media only to install the first site of a new hierarchy. For more information, see [Use the Setup Wizard to install sites](use-the-setup-wizard-to-install-sites).

    After this step, your top-level site runs the baseline version.
2. Use in-console updates to update your top-level site to a later version. Before you install any child sites or clients, update your top-level site to the update version that you plan to use. For more information, see [Updates for Configuration Manager](../../manage/updates).

    After this step, your top-level site runs the updated version.
3. If you intend for the first site to be a CAS, next install new child primary sites. Use the installation media from the CD.Latest folder on the CAS server to install child primary sites. Use this source media to make sure that new child primary sites match the version of the CAS. For more information, see [The CD.Latest folder for Configuration Manager](../../manage/the-cd.latest-folder).
4. Add other site system roles on remote servers at the CAS and primary sites. This action makes sure that the site systems run the updated version. For more information, see [Install site system roles](../configure/install-site-system-roles).
5. If you plan to have secondary sites, at each primary site, use the in-console option to install new secondary sites. Because you didn't install secondary sites while primary sites were at the baseline version, you don't need to update the secondary sites. Instead, you install new secondary sites that run the updated version. For more information, see [Install a secondary site](setup-wizard-secondary).
6. Install new clients at the primary site. Because you didn't install clients while primary sites were at the baseline version, you don't need to update clients. Instead, install new clients that run the updated version. For more information, see [Deploy clients](../../../clients/deploy/deploy-clients-to-windows-computers).
7. Install new consoles on remote computers. Because you didn't install consoles while primary sites were at the baseline version, you don't need to update consoles. Install them with the updated version. For more information, see [Install consoles](install-consoles).

## Upgrade to current branch

1. Upgrade your top-level System Center 2012 Configuration Manager site to a baseline version of the current branch. Use source media for Configuration Manager current branch. You always upgrade the top-level site of a hierarchy first, and then upgrade child sites. For more information, see [Upgrade to Configuration Manager](upgrade-to-configuration-manager).

    After this step, your top-level site runs the baseline version.
2. Upgrade each child primary site in your hierarchy to the same baseline version. When you upgrade from Microsoft System Center 2012 Configuration Manager, manually upgrade each primary site to a baseline version of the current branch. Don't upgrade secondary sites yet.

    After this step, each primary site runs the baseline version.
3. Set service windows on child-primary sites. After you upgrade all of your primary sites to the baseline version, configure maintenance windows to control when those sites install infrastructure updates. For more information, see [Service windows for site servers](../../manage/service-windows).

    - Child primary sites automatically install the same updates that you install at a CAS.
    - Secondary sties don't automatically install new versions. Update them manually from the console.

    After this step, child primary sites are ready to install updates during their service window.
4. Install the update version at your top-level site. This action updates your top-level site to the updated version. After a CAS installs the update version, each child primary site automatically installs the same update during its service window. For more information, see [Updates for Configuration Manager](../../manage/updates).

    After this step, your CAS and each primary site run the updated version.
5. Upgrade secondary sites. After a primary site installs the update, use the in-console option to update secondary sites. This action upgrades secondary sites directly from System Center 2012 Configuration Manager to the same update version as the primary site. For more information about upgrading a secondary site, see [Upgrade sites](upgrade-to-configuration-manager#upgrade-sites).
6. Upgrade clients. This process upgrades clients directly from System Center 2012 Configuration Manager to the update version that you installed at the primary site. For more information, see [How to upgrade clients for Windows computers](../../../clients/manage/upgrade/upgrade-clients-for-windows-computers).

    After this step, run the updated version.
7. Upgrade consoles on remote computers. This process upgrades clients directly from System Center 2012 Configuration Manager to the update version that you installed at the primary site. For more information, see [Install consoles](install-consoles).