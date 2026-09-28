---
layout: Conceptual
title: Hierarchy maintenance tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/hierarchy-maintenance-tool-preinst.exe
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
description: Understand what the hierarchy maintenance tool does, and why you might use it. Includes command-line options reference.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 81ff826f-0722-88ac-21c7-8a343bb46d68
document_version_independent_id: 5c026e42-c7f6-4e33-9a7b-5e3120619efd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/hierarchy-maintenance-tool-preinst.exe
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 16faed17-ccc9-85f5-f2d6-601c587b5dfa
---

# Hierarchy maintenance tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The hierarchy maintenance tool (Preinst.exe) passes commands to the Configuration Manager Hierarchy Manager while the Hierarchy Manager service is running. The hierarchy maintenance tool is automatically installed when you install a Configuration Manager site. You can find Preinst.exe in the `\bin\X64\00000409` folder on the site server.

Use the hierarchy maintenance tool in the following scenarios:

- When secure key exchange is required, there are situations where you need to manually do the initial public key exchange between sites. For more information, see Manually exchange public keys between sites.
- Remove active jobs for a destination site that's no longer available.
- Delete a site server from the Configuration Manager console when you can't uninstall it with setup. For example, if you physically remove a Configuration Manager site without first running setup to uninstall the site. The site information will still exist in the parent site's database, and the parent site will continue to attempt to communicate with the child site. To resolve this issue, run the hierarchy maintenance tool and manually delete the child site from the parent site's database.
- Stop all Configuration Manager services at a site without having to stop services individually.
- When you recover a site, use the `CHILDKEYS` option to distribute the public keys from multiple child sites to the recovering site.

To run the hierarchy maintenance tool, the current user needs administrative privileges on the local computer. Also, the user must explicitly have the **Administer** security right for the **Site** class. It's not sufficient that the user inherits this right by being a member of a group that has that permission.

## Hierarchy maintenance tool command-line options

When you use the hierarchy maintenance tool, you must run it locally on the central administration site (CAS), primary site, or secondary site server. Use the following syntax: `preinst.exe /<option>`. The following command-line options are available:

- `/DELJOB <SiteCode>`: Delete all jobs or commands from the current site to the specified destination site.
- `/DELSITE <ChildSiteCodeToRemove>`: Use this option at a parent site to delete the data for child sites from the site database of the parent site. Typically, you use this option if a site server computer is decommissioned before you uninstall the site from it.

    Note

    The `/DELSITE` option doesn't uninstall the site on the computer specified by the `ChildSiteCodeToRemove` parameter. This option only removes the site information from the Configuration Manager site database.
- `/DUMP <SiteCode>`: Use this option on the local site server to write site control images to the root folder of the drive on which the site is installed. You can write a specific site control image to the folder or write all site control files in the hierarchy.

    - `/DUMP <SiteCode>` writes the site control image only for the specified site.
    - `/DUMP` writes the site control files for all sites.

    An image is a binary representation of the site control file, which is stored in the Configuration Manager site database. The dumped site control file image is a sum of the base image plus the pending delta images.

    After dumping a site control file image with the hierarchy maintenance tool, the file name is in the format `sitectrl_<SiteCode>.ct0`.
- `/STOPSITE`: Use this option on the local site server to start a shutdown cycle for the Configuration Manager Site Component Manager service, which partially resets the site. When you start this shutdown cycle, it stops some Configuration Manager services on a site server and its remote site systems. It also flags these services for reinstallation. As a result of this shutdown cycle, some passwords are automatically changed when the services are reinstalled.

    Note

    If you want to see a record of shutdown, reinstallation, and password changes for Site Component Manager, enable logging for this component before using this command-line option.

    After the shutdown cycle is started, it proceeds automatically, skipping any non-responding components or computers. However, if the Site Component Manager service can't access a remote site system during the shutdown cycle, the components that are installed on the remote site system are reinstalled when the Site Component Manager service is restarted. When it's restarted, the Site Component Manager service repeatedly attempts reinstallation of all services that are flagged for reinstallation until it's successful.

    You can restart the Site Component Manager service using Service Manager. After it restarts, all affected services are uninstalled, reinstalled, and restarted. After you use the `/STOPSITE` option to start the shutdown cycle, you can't avoid the reinstallation cycles after the Site Component Manager service is restarted.
- `/KEYFORPARENT`: Distribute the site's public key to a parent site.

    The `/KEYFORPARENT` option places the public key of the site in the file `<SiteCode>.CT4` at the root of the program files drive. After you run preinst.exe with this option, manually copy this file to the parent site's `\Inboxes\hman.box` folder (not `hman.box\pubkey`).
- `/KEYFORCHILD`: Distribute the site's public key to a child site.

    The `/KEYFORCHILD` option places the public key of the site in the file `<SiteCode>.CT5` at the root of the program files drive. After you run preinst.exe with this option, manually copy this file to the child site's `\Inboxes\hman.box` folder (not `hman.box\pubkey`).
- `/CHILDKEYS`: Use this option on the child sites of a site that you're recovering. It distributes public keys from multiple child sites to the recovering site.

    The `/CHILDKEYS` option places the key from the site where you run the option and all of that sites child sites public keys into the file `<SiteCode>.CT6`. After you run preinst.exe with this option, manually copy this file to the recovering site's `\Inboxes\hman.box` folder (not `hman.box\pubkey`).
- `/PARENTKEYS`: Use this option on the parent site of a site that you're recovering. It distributes public keys from all parent sites to the recovering site.

    The `/PARENTKEYS` option places the key from the site where you run the option and the keys from each parent site above that site into the file `<SiteCode>.CT7`. After you run preinst.exe with this option, manually copy this file to the recovering site's `\Inboxes\hman.box` folder (not `hman.box\pubkey`).

## Manually exchange public keys between sites

By default, the **Require secure key exchange** option is enabled for Configuration Manager sites. When secure key exchange is required, there are two situations when you need to manually do the initial key exchange between sites:

- If you haven't extended the Active Directory schema for Configuration Manager
- Configuration Manager sites aren't publishing site data to Active Directory

You can use the hierarchy maintenance tool to export the public keys for each site. Once exported, then manually exchange the keys between the sites.

Note

After the public keys are manually exchanged, review the **hman.log** log file on the parent site server. This log file records site configuration changes and site information publication to Active Directory. You can make sure that the primary site has processed the new public key.

### How to manually transfer the child site public key to the parent site

1. Sign in to the child site server, open a command prompt, and navigate to the location of **Preinst.exe**.
2. Type the following command to export the child site's public key: `Preinst /keyforparent`

The `/keyforparent` option places the public key of the child site in the `<SiteCode>.CT4` file located at the root of the system drive.

1. Move the `<SiteCode>.CT4` file to the parent site's `\inboxes\hman.box` folder in the Configuration Manager installation directory.

### How to manually transfer the parent site public key to the child site

1. Sign in to the parent site server, open a command prompt, and navigate to the location of **Preinst.exe**.
2. Type the following command to export the parent site's public key: `Preinst /keyforchild`

The `/keyforchild` option places the public key of the parent site in the `<SiteCode>.CT5` file located at the root of the system drive.

1. Move the `<SiteCode>.CT5` file to the child site's `\inboxes\hman.box` folder in the Configuration Manager installation directory.