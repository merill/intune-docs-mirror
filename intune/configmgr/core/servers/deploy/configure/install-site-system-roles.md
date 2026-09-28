---
layout: Conceptual
title: Install site system roles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-site-system-roles
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
description: Add site system roles to an existing or new site system server in the site.
ms.date: 2020-04-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 149bcef1-c359-4602-8361-a5ed6d55c14d
document_version_independent_id: 39c2806b-fa5f-3989-d572-47f983f22a7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/install-site-system-roles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/install-site-system-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/install-site-system-roles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: fd8d0f65-1889-3a7b-a11f-fb43e5d4f09c
---

# Install site system roles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

There are two methods in the Configuration Manager console to install site system roles:

- **Add Site System Roles**: Add site system roles to an existing site system server in the site.
- **Create Site System Server**: Specify a new server as a site system server, and then install one or more roles. This method is the same as the **Add Site System Roles**, except for the first page. You first specify the name of the server and the site in which you want to install it.

Tip

A best practice for security and operational resilience is to keep site system roles separate from the site server, rather than colocate them on the same computer. When you install a role on a remote computer, Configuration Manager adds the computer account of the remote computer to a local group on the site server.

When you install the site on a domain controller, the group on the site server is a domain group instead of a local group. In this case, the remote site system role doesn't immediately work. The site system server needs to restart, or you refresh the Kerberos ticket for the remote server's computer account. For more information, see [Accounts used](../../../plan-design/hierarchy/accounts).

Before it installs the site system role, Configuration Manager checks the destination computer to make sure it meets the prerequisites for the selected roles.

By default, when Configuration Manager installs a site system role, it installs files on the first available NTFS-formatted disk drive that has the most available free disk space. To prevent Configuration Manager from installing on specific drives, before you install the site system server, create an empty file named **NO\_SMS\_ON\_DRIVE.SMS** in the root of the drive.

Configuration Manager uses the **site system installation account** to install roles. You specify this account when you install the role. By default, this account is the local system account of the site server computer. You can specify a domain user account as the site system installation account. For more information, see [Accounts - Site system installation account](../../../plan-design/hierarchy/accounts#site-system-installation-account).

## Install roles on an existing site system server

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Site Configuration**, and select the **Servers and Site System Roles** node. Select the existing site system server on which you want to install new site system roles.
2. In the ribbon, on the **Home** tab, in the **Server** group, select **Add Site System Roles**.
3. On the **General** page, review the settings.

    Tip

    To access the site system role from the internet, make sure that you specify an internet fully qualified domain name (FQDN).
4. On the **Proxy** page, if roles on this server require an internet proxy, then specify settings for a proxy server. For more information, see [Proxy server support](../../../plan-design/network/proxy-server-support).
5. On the **System Role Selection** page, select the site system roles that you want to add.
6. Complete the wizard. Additional pages can appear for specific roles. For more information, see [Configuration options for site system roles](configuration-options-for-site-system-roles).

Tip

The Windows PowerShell cmdlet, **New-CMSiteSystemServer**, performs the same function as this procedure. For more information, see [New-CMSiteSystemServer](/en-us/powershell/module/configurationmanager/new-cmsitesystemserver).

## Install roles on a new site system server

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Site Configuration**, and select the **Servers and Site System Roles** node.
2. In the ribbon, on the **Home** tab, in the **Create** group, select **Create Site System Server**.
3. On the **General** page, specify the general settings for the site system.

    Tip

    To access the new site system role from the internet, make sure that you specify an internet FQDN.
4. On the **Proxy** page, if roles on this server require an internet proxy, then specify settings for a proxy server. For more information, see [Proxy server support](../../../plan-design/network/proxy-server-support).
5. On the **System Role Selection** page, select the site system roles that you want to add.
6. Complete the wizard. Additional pages can appear for specific roles. For more information, see [Configuration options for site system roles](configuration-options-for-site-system-roles).

Tip

The Windows PowerShell cmdlet, **New-CMSiteSystemServer**, performs the same function as this procedure. For more information, see [New-CMSiteSystemServer](/en-us/powershell/module/configurationmanager/new-cmsitesystemserver).