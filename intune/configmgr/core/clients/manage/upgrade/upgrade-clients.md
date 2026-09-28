---
layout: Conceptual
title: Upgrade clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients
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
description: Get information about how to upgrade clients in Configuration Manager.
ms.date: 2021-07-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: b482eae3-f456-4e8e-e069-b52efe0c1464
document_version_independent_id: 9ca9dccf-89fa-1660-e6ab-97bb33243083
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/upgrade/upgrade-clients.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/upgrade/upgrade-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/upgrade/upgrade-clients.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8884de41-90e6-d1c8-f5d8-f3b30cc0c37b
---

# Upgrade clients - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use different methods to upgrade the Configuration Manager client software on Windows computers and Mac computers. Here are the advantages and disadvantages of each method.

Tip

If you are upgrading your server infrastructure from System Center 2012 Configuration Manager, before upgrading the Configuration Manager clients, complete the server upgrades including installing all current branch updates. This process makes sure that you'll have the most recent version of the client software.

## Group Policy installation

Supported client platform: **Windows**

Advantages:

- Doesn't require computers to be discovered before the client can be upgraded.
- Can be used for new client installations or for upgrades.
- Computers can read client installation properties that have been published to Active Directory Domain Services.
- Doesn't require you to configure and maintain an installation account for the intended client computer.

Disadvantages:

- Can cause high network traffic if you're upgrading many clients.
- If you don't extend the Active Directory schema for Configuration Manager, use [Group Policy settings](../../deploy/deploy-clients-to-windows-computers#BKMK_ClientGP). These settings add client installation properties to computers in your site.

## Logon script installation

Supported client platform: **Windows**

Advantages:

- Doesn't require computers to be discovered before the client can be installed.
- Can be used for new client installations or for upgrades.
- Supports using command-line properties for CCMSetup.

Disadvantages:

- Can cause high network traffic if you're upgrading many clients in a short time.
- Can take a long time to upgrade all client computers if users don't frequently sign in to the network.

For more information, see [How to install clients by using logon scripts](../../deploy/deploy-clients-to-windows-computers#BKMK_ClientLogonScript).

## Manual installation

Supported client platform: **Windows**, **macOS**

Advantages:

- Doesn't require computers to be discovered before the client can be upgraded.
- Can be useful for testing purposes.
- Supports using command-line properties for CCMSetup.

Disadvantages:

- No automation, so can be time consuming.

For more information, see the following articles:

- [How to install clients manually](../../deploy/deploy-clients-to-windows-computers#BKMK_Manual)
- [How to upgrade clients on Mac computers](upgrade-clients-on-mac-computers)

## Upgrade installation (application management)

Supported client platform: **Windows**

Advantages:

- Supports using command-line properties for CCMSetup.

Disadvantages:

- Can cause high network traffic if you distribute the client to large collections.
- Can only be used to upgrade the client software on computers that have been discovered and assigned to the site.

For more information, see [How to install clients by using a package and program](../../deploy/deploy-clients-to-windows-computers#BKMK_ClientApp).

## Automatic client upgrade

Supported client platform: **Windows**

Advantages:

- Because of the randomization over the specified period, only auto-upgrade is suitable for large-scale client upgrades. Other methods are either too slow on large scale, or don't have randomization.

    Note

    Client piloting isn't good for large scale as it doesn't randomize at all.
- Can be used to automatically keep clients in your site at the latest version.
- Requires minimal administration.

Disadvantages:

- Can only be used to upgrade the client software and can't be used to install a new client.
- Applies to all clients in the hierarchy that are assigned to a site. Can't be scoped by collection.
- Limited scheduling options.

For more information, see [How to upgrade clients for Windows computers](upgrade-clients-for-windows-computers).

## Client testing

Supported client platform: **Windows**

Advantages:

- Can be used to test new client versions in a smaller pre-production collection.
- When testing is complete, clients in pre-production are promoted to production and automatically upgraded across the Configuration Manager site.

Disadvantages:

- Can only be used to upgrade the client software and can't be used to install a new client.

For more information, see [How to test client upgrades in a pre-production collection](test-client-upgrades).