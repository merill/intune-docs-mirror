---
layout: Conceptual
title: Websites for site systems - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/websites-for-site-system-servers
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
description: Learn about default and custom websites for site system servers in Configuration Manager.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: bbfc4cf2-66c2-5bd6-e8ee-21f716c394bf
document_version_independent_id: 675e37a8-0e93-2a04-f645-6aa73ab385e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/network/websites-for-site-system-servers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/network/websites-for-site-system-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/network/websites-for-site-system-servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: 7bcc7f7d-4e93-b82f-bbe0-d61572279842
---

# Websites for site systems - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Several Configuration Manager site system roles require the use of Internet Information Services (IIS). By default, they use the default IIS website to host site system services. When you run other web applications on the same server, and settings aren't compatible with Configuration Manager, consider using a custom website for Configuration Manager.

Tip

For improved security, dedicate a server for the Configuration Manager site systems that require IIS. When you run other applications on a Configuration Manager site system, you increase the attack surface of that computer.

## Choosing to use custom websites

By default, site system roles use the **Default Web Site** in IIS. This configuration is set up automatically when the site system role installs. However, at primary sites, you can choose to use custom websites instead.

When you use custom websites:

- They're enabled for the entire site instead of for individual site system servers or roles.
- At primary sites, for each computer that will host an applicable site system role, configure it with a custom website named **SMSWEB**. Until you create this website, and set up site system roles on that computer to use the custom website, clients can't communicate with site system roles on that computer.
- Secondary sites are automatically set up to use a custom website when their primary parent site uses it. Create custom websites in IIS on each secondary site system server that requires IIS.

### Prerequisites for using custom websites

Before you enable the option to use custom websites at a site:

- Create a custom website named **SMSWEB** in IIS on each site system server that requires IIS. Set this configuration at the primary site and at any child secondary sites.
- Set up the custom website to respond to the same port that you set up for Configuration Manager client communication. This port is known as the *client request port*.
- For each custom or default website that uses a custom folder, place a copy of the default document type that you use in the root folder that hosts the website. For example, with the typical default configuration, **iisstart.htm** is one of several default document types that are available. You can find this file in the root of the default website. Place a copy of this file or other default document in the root folder that hosts the SMSWEB custom website. For more information about default document types, see [Default Document for IIS](/en-us/iis/configuration/system.webServer/defaultDocument/).

### About IIS requirements

The following site system roles require IIS and a website to host the site system services:

- Distribution point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Software update point
- State migration point

Other considerations:

- When a primary site has custom websites enabled, clients that are assigned to that site are directed to communicate with the custom websites instead of the default websites.
- If you use custom websites for one primary site, consider custom websites for all primary sites in your hierarchy. This configuration makes sure that clients can successfully roam within the hierarchy. *Roaming* is when a client computer moves to a new network segment that is managed by a different site. Roaming can affect resources that a client can access locally instead of across a WAN link.
- Site system roles that use IIS but don't accept client connections also use the SMSWEB website instead of the default website. For example, the reporting services point.
- Custom websites require you to assign port numbers that differ from the computer's default website. A default website and custom website can't run at the same time if both websites try to use the same TCP/IP ports.
- The TCP/IP ports that you set up in IIS for the custom website must match the client request ports for the site.

## Switch between default and custom websites

Although you can check or uncheck the box for using custom websites at a primary site at any time, plan carefully before you make this change. When this configuration changes, all applicable site system roles at the primary site and child secondary sites uninstall and then reinstall.

The following roles reinstall automatically:

- Management point
- Distribution point
- Software update point
- Fallback status point
- State migration point

You need to manually reinstall the following roles:

- Enrollment point
- Enrollment proxy point

When you change from the default website to use a custom website, Configuration Manager doesn't remove the old virtual directories. If you want to remove the files that Configuration Manager used, manually delete the virtual directories that were created under the default website.

If you change the site to use custom websites, clients that are already assigned to the site need to be reconfigured to use the new client request ports for the custom websites. For more information, see [How to configure client communication ports](../../clients/deploy/configure-client-communication-ports).

## Set up custom websites

The steps to create a custom website vary for different OS versions. For exact steps, refer to the documentation for your OS version.

Use the following general information when applicable:

- The website name is **SMSWEB**.
- When you set up HTTPS, specify a PKI certificate before you can save the configuration.
- After you create the custom website, remove the custom website ports that you use from other websites in IIS:

    1. Edit the **Bindings** of the other websites to remove ports that match the ports that are assigned to the **SMSWEB** website.
    2. Start the **SMSWEB** website.
    3. Restart the **SMS\_SITE\_COMPONENT\_MANAGER** service on the site server of the site.