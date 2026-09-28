---
layout: Conceptual
title: Client installation methods - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/client-installation-methods
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
description: Learn about the methods of installing the Configuration Manager client.
ms.date: 2024-10-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: c901582c-2b76-bc8e-929b-b173f30e161c
document_version_independent_id: 28df8998-d9ab-d2de-9491-c39ea33deed5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/plan/client-installation-methods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/plan/client-installation-methods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/plan/client-installation-methods.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: c3376665-dbbe-628d-d117-87aedccbbd87
---

# Client installation methods - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use different methods to install the Configuration Manager client software. Use one method, or a combination of methods. This article describes each method, so you can learn which one works best for your organization.

## Client push installation

**Supported client platform**: Windows

#### Advantages

- Can be used to install the client on a single computer, a collection of computers, or to the results from a query.
- Can be used to automatically install the client on all discovered computers.
- Automatically uses client installation properties defined on the **Client** tab in the **Client Push Installation Properties** dialog box.

#### Disadvantages

- Can cause high network traffic when pushing to large collections.
- Can only be used on computers that have been discovered by Configuration Manager.
- Can't be used to install clients in a workgroup.
- A client push installation account must be specified that has administrative rights to the intended client computer.
- Windows Firewall must be configured with exceptions on client computers.
- You can't cancel client push installation. Configuration Manager tries to install the client on all discovered resources. It retries any failures for up to seven days.

For more information, see [How to install clients with client push](../deploy-clients-to-windows-computers#BKMK_ClientPush).

## Software update point-based installation

**Supported client platform**: Windows

#### Advantages

- Can use your existing software updates infrastructure to manage the client software.
- If Windows Server Update Services (WSUS) and group policy settings in Active Directory Domain Services are configured correctly, it can automatically install the client software on new computers.
- Doesn't require computers to be discovered before the client can be installed.
- Computers can read client installation properties that have been published to Active Directory Domain Services.
- If the client is removed, this method reinstalls it.
- Doesn't require you to configure and maintain an installation account for the intended client computer.

#### Disadvantages

- Requires a functioning software updates infrastructure as a prerequisite.
- Must use the same server for client installation and software updates. This server must reside in a primary site.
- To install new clients, you must configure a group policy object in Active Directory Domain Services with the client's active software update point and port.
- If the Active Directory schema isn't extended for Configuration Manager, you must use group policy settings to provision computers with client installation properties.

For more information, see [How to install clients with software update-based installation](../deploy-clients-to-windows-computers#BKMK_ClientSUP).

## Group policy installation

**Supported client platform**: Windows

#### Advantages

- Doesn't require computers to be discovered before the client can be installed.
- Can be used for new client installations or for upgrades.
- Computers can read client installation properties that have been published to Active Directory Domain Services.
- Doesn't require you to configure and maintain an installation account for the intended client computer.

#### Disadvantages

- If a large number of clients are being installed, it can cause high network traffic.
- If the Active Directory schema isn't extended for Configuration Manager, you must use group policy settings to add client installation properties to computers in your site.

For more information, see [How to install clients with group policy](../deploy-clients-to-windows-computers#BKMK_ClientGP).

## Logon script installation

**Supported client platform**: Windows

#### Advantages

- Doesn't require computers to be discovered before the client can be installed.
- Supports using command-line properties for CCMSetup.

#### Disadvantages

- If a large number of clients are being installed over a short time period, it can cause high network traffic.
- If users don't frequently log on to the network, it can take a long time to install on all client computers.

For more information, see [How to install clients with logon scripts](../deploy-clients-to-windows-computers#BKMK_ClientLogonScript).

## Manual installation

**Supported client platform**: Windows, macOS X

#### Advantages

- Doesn't require computers to be discovered before the client can be installed.
- Can be useful for testing purposes.
- Supports using command-line properties for CCMSetup.

#### Disadvantages

- No automation, therefore time consuming.

For more information about how to manually install the client on each of platform, see the following articles:

- [How to deploy clients to Windows computers](../deploy-clients-to-windows-computers#BKMK_Manual)
- [How to deploy clients to Macs](../deploy-clients-to-macs)

## Microsoft Intune MDM installation

**Supported client platforms**: Windows 10 or later

#### Advantages

- Doesn't require computers to be discovered before the client can be installed.
- Doesn't require you to configure and maintain an installation account for the intended client computer.
- Can use modern authentication with Microsoft Entra ID.
- Can install and assign computers on the internet.
- Can automate with Windows Autopilot and Microsoft Intune for co-management.

#### Disadvantages

- Requires additional technologies outside of Configuration Manager.
- Requires the device have access to the internet, even if it is not internet-based.

For more information, see the following articles:

- [How to install clients to Intune MDM-managed Windows devices](../deploy-clients-to-windows-computers#bkmk_mdm)
- [Install and assign Configuration Manager clients using Microsoft Entra ID for authentication](../deploy-clients-cmg-azure)