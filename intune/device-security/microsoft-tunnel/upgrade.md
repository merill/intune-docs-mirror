---
layout: Conceptual
title: Upgrade the Microsoft Tunnel Gateway server software - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/upgrade
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-infrastructure
ms.reviewer: ochukwunyere
ms.subservice: protect
description: Understand how Microsoft Tunnel Gateway upgrades to new versions of the tunnel software for Microsoft Intune.
ms.date: 2026-09-22T00:00:00.0000000Z
ms.topic: how-to
ms.custom: msecd-doc-authoring-1028
ai-usage: ai-assisted
locale: en-us
document_id: 0c11d6eb-282a-9313-0aae-12cd76adac5a
document_version_independent_id: 0c11d6eb-282a-9313-0aae-12cd76adac5a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/microsoft-tunnel/upgrade.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/microsoft-tunnel/upgrade
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/microsoft-tunnel/upgrade.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 53e04f38-a9d0-e52d-97e6-a1df056bb955
---

# Upgrade the Microsoft Tunnel Gateway server software - Microsoft Intune | Microsoft Learn

Microsoft Tunnel, a VPN gateway solution for Microsoft Intune, periodically receives software upgrades, which must install on the tunnel servers to keep them in support. To stay in support, servers must run the most recent release, or at most be one version behind. The information in this article explains:

- The upgrade process
- Upgrade controls
- Status reports you can use to understand the software version of tunnel servers
- When upgrades are available
- How to control when upgrades happen.

Intune handles the upgrade of servers assigned to each tunnel site for you. When you start the upgrade for site, all servers in the site upgrade one at a time, which is referred to as an upgrade cycle. While a server is upgrading, the Microsoft Tunnel on that server isn't available for use. Upgrading a single server at a time helps minimize disruptions to users when the site includes multiple servers.

During an upgrade cycle:

- Intune begins by upgrading one server in the site. The upgrade can start as soon as 10 minutes after the release becomes available.
- If a server was off, upgrade begins after the server turns on.
- After a successful upgrade of one server at a site, Intune waits a short time before it starts the upgrade of the next server.

## Use upgrade controls

To help control when Intune starts the upgrade cycle, configure the following settings at each site. You can configure the settings when [creating a new site](install#create-a-site), or by editing the properties of an existing site:

- **Automatically upgrade servers at this site**
- **Limit server upgrades to maintenance window**

### Automatically upgrade servers at this site

This setting determines if an upgrade cycle for the site can begin automatically, or if an admin must explicitly approve the upgrade before the cycle can begin.

- **Yes***(default)* – When set to *Yes*, the site automatically upgrade servers as soon as possible after a new tunnel version becomes available. Upgrades begin without admin intervention.

    If you set a maintenance window for the site, the upgrade cycle begins between the windows start and end time. When no maintenance window is set, the upgrade cycle starts as soon as possible.
- **No** – When set to *No*, Intune doesn't upgrade servers until an admin explicitly chooses to begin the upgrade cycle.

    After upgrade is approved for a site with a maintenance window, the upgrade cycle begins between the windows start and end time. If there's no maintenance window, the upgrade cycle starts as soon as possible.

    Important

    When you configure site for manual upgrades, periodically review the Health check tab to understand when newer versions of Microsoft Tunnel are available to install. The report also identifies when the current tunnel version at the site is out of support.

### Limit server upgrades to maintenance window

Use this setting to define a maintenance window for the site.

When configured for site, the server upgrade cycle can begin only during the configured period. However, once begun, the cycle continues to update servers one-by-one until all servers assigned to the site complete the upgrade.

- **No***(default)* – No maintenance window is set. Sites that are configured to upgrade automatically do so as soon as possible. Sites configured to require explicit action to start the upgrade will do so as soon as possible *after* the upgrade is approved.
- **Yes** – Set a maintenance window. The window limits when a server upgrade cycle can begin at the site. The maintenance window doesn’t define when individual servers assigned to the site might start to upgrade.

    Sites that are configured to upgrade automatically start the upgrade cycle only during the configured period. Sites configured to require the admin to approve the upgrade before beginning, will do during the next maintenance window *after* the upgrade is approved.

    When set to *Yes*, configure the following options:

    - **Time zone** – The time zone you select determines when the maintenance window starts and ends on all servers in the site. The time zone of individual servers isn't used.
    - **Start time** – Specify the earliest time that the upgrade cycle can start, based on the time zone you selected.
    - **End time** - Specify the latest time that upgrade cycle can start, based on the time zone you selected. Upgrade cycles that start before this time will continue to run and can complete after this time.

## View tunnel server status

You can view information about the status of Microsoft Tunnel servers, including the version of Microsoft Tunnel on a server.

For sites that don't support automatic upgrade, you can also view when upgrades to a new version are available.

Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Tenant administration** &gt; **Microsoft Tunnel Gateway** &gt; **Health status**. Select a server and then open the **Health check** tab to view the following information about it:

- **Server version** - The status of the Tunnel Gateway Server software, in the context of the most recent version available.

    - **Healthy** - Up to date with the most recent software version.
    - **Warning** - One version behind.
    - **Unhealthy** - Two or more versions behind, and out of support.

When a server doesn’t run the most recent software version, plan to install an available upgrade to keep the Microsoft Tunnel in support.

## Approve upgrades

Sites that have the setting *Automatically upgrade servers at this site* set to *No* don't automatically upgrade servers. Instead, an admin must approve upgrades for servers at that site before the upgrade cycle starts.

To understand when an upgrade is available for servers, use the Health check tab to review server status.

### To approve an upgrade

1. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Tenant administration** &gt; **Microsoft Tunnel Gateway** &gt; **Sites**.
2. Select the site with an **Upgrade type** of **Manual**.
3. On the site’s properties, select **Upgrade servers**.

After you choose to upgrade servers, Intune starts the process to do so, which can't be canceled. The time that upgrades begin at the site depends on the configuration of maintenance windows for the site.

## Understanding version identifiers

Microsoft Tunnel uses two types of identifiers for container image versions:

- **Version Number Labels**: Human-readable identifiers that represent the build date and sequence or version of an update. For example, version 20251126.1 represents version 1 for a build created on November 26, 2025.
- **SHA256 Digests**: Cryptographic hashes that provide precise identification and validation for update deployment.

Version number labels are internal identifiers applied during the build process that help customers and Microsoft support teams quickly identify specific releases. These labels complement the SHA256 digests that are used for actual deployment and validation.

While SHA256 digests remain the official reference for deployment precision, you can use version labels to:

- Reference releases in automation scripts and deployment pipelines
- Simplify inventory management and compliance reporting
- Streamline communication with Microsoft support when discussing specific releases
- Validate that deployed images match expected release dates and sequences

The Microsoft Tunnel version for a server isn't available in the Intune UI at this time. Instead, run the following command on the Linux server that hosts the tunnel to identify the hash values of *agentImageDigest* and *serverImageDigest*: `cat /etc/mstunnel/images_configured`

## Microsoft Tunnel update history

Updates for the Microsoft Tunnel release periodically. When a new version is available, read about the changes here.

After an update releases, it rolls out to tenants over the following days. This rollout time means new updates might not be available for your tunnel servers for a few days.

Important

Container releases take place in stages. If you notice that your container images aren't the most recent, please be assured that they will be updated and delivered within the following week.

### September 9, 2026

Version Number: 20260909.1

Image hash values:

- **agentImageDigest**: sha256:d0954b46159ffd2298f0d7d203e319c1ec8b72b7d91fe311de7325e67d120df1
- **serverImageDigest**: sha256:e4af24ca5569d263ec019bba6fe17f8e243f9c459406ac1ba7580de1d8c09cee

### August 18, 2026

Version Number: 20260818.1

Image hash values:

- **agentImageDigest**: sha256:912d945c1ed1a6ca5ad501daaa4ddb04cc07286c0c02a44d2625a2f2eb5321c2
- **serverImageDigest**: sha256:19a40bb9965bcc7978a160ced8d54cab4bc6ba59cd94373ed24dd817be6a2297

Changes in this release:

- Minor bug fixes
- Package and security updates

### July 27, 2026

Version Number: 20260624.1

Image hash values:

- **agentImageDigest**: sha256:9a7316aaea439dd634b7e073dccc44977e2bb8cdbbf3245cc6288b7932334721
- **serverImageDigest**: sha256:fa286ab658830ded388d839b17420c13cf7fb076f806701d76d7e6867f83859b

Changes in this release:

- Minor Bug fixes

### May 27, 2026

Version Number: 20260527.1

Image hash values:

- **agentImageDigest**: sha256:1a814670dd9848ddb3ee7831fefa39f195f854c7e03c825b9fb9e4631544940f
- **serverImageDigest**: sha256:89242bab502fe0b49023a48fc0a8ef20b9ca6ef0336b852aa8166fd7b542a590

Changes in this release:

- Package and security updates

### May 13, 2026

Version Number: 20260513.1

Image hash values:

- **agentImageDigest**: sha256:e2e526dff65cd9693483147e523543957de1baa892260cdb3d5423dba050d08b
- **serverImageDigest**: sha256:a27cd376fbdcdfe54aeaa0f0b662f59da6630faa0a28856c7170feaf8def5d18

Changes in this release:

- Package and security updates

### May 7, 2026

Version Number: 20260507.2

Image hash values:

- **agentImageDigest**: sha256:fc8a3c599c36073affe234feaf57b619441317faaa5c1090df3c3e40d6f70a57
- **serverImageDigest**: sha256:f53affd23ba2fa9fc5fbcc0d1446c7a1437541b6bacfe246d62aa8ce34c1e3a6

Changes in this release:

- Package updates

### March 30, 2026

Version Number: 20260330.1

Image hash values:

- **agentImageDigest**: sha256:163214b94af6d91a5ef02690f891c5a41e87b1059b9530324716ee34778c1785
- **serverImageDigest**: sha256:dd62c292528e8e5aa4e7b84418efa42fd3830ec0db40467947cde8125aa17d7e

Changes in this release:

- Major bug fixes

### February 5, 2026

Version Number: 20251219.1-01

Image hash values:

- **agentImageDigest**: sha256:2859a8e1466f002458e001baf902c89a0fba1277b8f8dc6480e84bc946848a2d
- **serverImageDigest**: sha256:34aee0978f7cb991d2c6baa5adc27b052e54d6cb0d73b637cccd0d565addf619

Changes in this release:

- Minor bug fixes