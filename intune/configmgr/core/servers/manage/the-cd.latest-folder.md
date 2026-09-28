---
layout: Conceptual
title: The `CD.Latest` folder - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/the-cd.latest-folder
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
description: Learn about the process that delivers updates to the product from within the Configuration Manager console.
ms.date: 2022-03-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f1bbae03-5055-02d6-2ab5-e9083d52123f
document_version_independent_id: 62cdf991-b675-ed30-1d74-469ec914284f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/the-cd.latest-folder.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/the-cd.latest-folder
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/the-cd.latest-folder.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 74043b3f-e432-d579-ebfb-cb9c13a1ecfe
---

# The `CD.Latest` folder - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager has a process to deliver updates to the product from within the Configuration Manager console. To support this new method of updating Configuration Manager, a new folder is created named `CD.Latest`. This folder contains a copy of the Configuration Manager installation files for the updated version of your site.

The `CD.Latest` folder contains a folder named `Redist`, which contains the redistributable files that setup downloads and uses. These files are matched to the version of Configuration Manager files found in that `CD.Latest` folder. When you run Setup from a `CD.Latest` folder, you must use files that are matched to that version of Setup. You can either direct Setup to download new and current files from Microsoft, or direct Setup to use the files from the Redist folder included in the `CD.Latest` folder.

Baseline media doesn't include a `Redist` folder. The site doesn't create a Redist folder until you install an in-console update. In the meantime, use the Redist folder that you used when installing sites from the baseline media.

Tip

Make sure the redistributable files you use are current. If you haven't recently downloaded redistributable files, plan to allow Setup to do so from Microsoft.

The following scenarios create or update the `CD.Latest` folder on a central administration site or primary site server:

- When you install an update or hotfix from within the Configuration Manager console, the site creates or updates the folder in the Configuration Manager installation folder.
- When you run the built-in Configuration Manager backup task, the site creates or updates the folder under the designated backup folder location.
- When you install a new site using baseline media, the site creates the `CD.Latest` folder.

## Supported scenarios

The source files from the `CD.Latest` folder are supported for the following scenarios:

### Backup and recovery

To recover a site, use the source files from a `CD.Latest` folder that matches your site. When you run a site backup using the built-in site backup task, the `CD.Latest` folder is included as part of the backup.

- When you reinstall a site as part of a site recovery, you install the site from the `CD.Latest` folder included in your backup. This action installs the site using the file versions that match your site backup and site database.

    - If you don't have access to the correct `CD.Latest` folder version, get the `CD.Latest` folder with the correct file versions by installing a site in a lab environment. Then update that site to match the version you want to recover.
    - If you don't have the correct `CD.Latest` folder and its contents available, you can't recover a site. In this circumstance, you need to reinstall the site.
- When you don't have a `CD.Latest` folder, but do have a working child primary site or central administration site, you can use that site as a reference site for a site recovery.

### Install a child primary site

When you want to install a new child primary site below a central administration site that has installed one or more in-console updates, use Setup and the source files from the `CD.Latest` folder from the central administration site. This process uses installation source files that match the version of the central administration site. For more information, see [Use the Setup Wizard to install sites](../deploy/install/use-the-setup-wizard-to-install-sites).

### Expand a stand-alone primary site

When you expand a stand-alone primary site by installing a new central administration site, use Setup and the source files from the `CD.Latest` folder from the primary site. This process uses installation source files that match the version of the primary site. For more information, see [Expand a stand-alone primary site](../deploy/install/setup-wizard-central-primary#expand-a-stand-alone-primary-site).

### Install a secondary site

When you want to install a new secondary site below a primary site that has installed one or more in-console updates, use the source files from the `CD.Latest` folder from the primary site.

For more information, see [Install a secondary site](../deploy/install/setup-wizard-secondary).

## Unsupported scenarios

The updated `CD.Latest` source files aren't supported for:

- Installing a new site for a new hierarchy
- Upgrading a Microsoft System Center 2012 Configuration Manager site to Configuration Manager current branch
- Installing Configuration Manager clients
- Installing Configuration Manager consoles