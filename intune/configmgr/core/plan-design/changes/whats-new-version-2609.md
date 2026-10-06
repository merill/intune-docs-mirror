---
layout: Conceptual
title: What's new in version 2609 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-version-2609
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
description: Get details about changes and new capabilities introduced in version 2609 of Configuration Manager current branch.
ms.date: 2026-09-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: c0c645d7-85d6-25a3-a15c-9697d5e3e7c5
document_version_independent_id: c0c645d7-85d6-25a3-a15c-9697d5e3e7c5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-version-2609.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-version-2609
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-version-2609.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6874d271-6880-ebd8-df0a-32a42613aa18
---

# What's new in version 2609 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2609 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2503 or later.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2609](../../servers/manage/checklist-for-installing-update-2609). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2609#post-update-checklist).

To take full advantage of new Configuration Manager changes, after you update the site, also update clients to the latest version. New functionality appears in the Configuration Manager console when you update the site and console, but the complete scenario isn't functional until the client version is also the latest.

For a list of significant customer-reported issues resolved in this release, see the [Summary of changes in Configuration Manager version 2609](../../../hotfix/2609/2377842) knowledge base article.

## Site infrastructure

### Prerequisite warning for automatic approval of all clients

The upgrade prerequisite check warns when the client approval method is set to **Automatically approve all computers (not recommended)**. This check is a warning and doesn't block the upgrade.

Important

The **Automatically approve all computers (not recommended)** option is planned for removal in a future release because it allows untrusted computers to be approved without administrator review. We strongly recommend that you stop using this option as soon as possible. In **Hierarchy Settings**, change the client approval method to manual approval or automatic approval for computers in trusted domains.

For more information, see [Insecure client approval method](../../servers/deploy/install/list-of-prerequisite-checks#insecure-client-approval-method).

### SQLCLR assemblies no longer require TRUSTWORTHY

The site database no longer requires the **TRUSTWORTHY** property to load Configuration Manager SQLCLR assemblies, including when you use SQL Server Always On availability groups. Configuration Manager also verifies that its SQLCLR assemblies are Microsoft-signed.

For configuration details, see [SQLCLR assembly trust](../configs/supported-configurations-for-sql-server#sqlclr-assembly-trust).

## Supported platforms and dependencies

### Windows Server 2012 and 2012 R2 client support removed

Configuration Manager no longer supports Windows Server 2012, Windows Server 2012 R2, or their Windows Storage Server editions as client operating systems.

Upgrade devices to a supported Windows Server version. For more information, see [Supported OS versions for clients and devices](../configs/supported-operating-systems-for-clients-and-devices).

### Configuration Manager no longer supports SQL Server 2016

Starting with version 2609, Configuration Manager no longer supports SQL Server 2016 (Standard, Enterprise, and Express editions). SQL Server 2016 extended support ended in July 2026. Upgrade to a supported SQL Server version — at minimum, SQL Server 2017 (Cumulative Update 2 or later). If you don't upgrade, Configuration Manager upgrades are blocked and you see an error during the prerequisite check.

This minimum applies to site databases at central administration sites, primary sites, and secondary sites, including SQL Server Express at secondary sites. The prerequisite check blocks site installation or update when the SQL Server version is below this minimum.

For more information, see [Supported SQL Server versions for Configuration Manager](../configs/support-for-sql-server-versions).

### SQL Server drivers updated

Configuration Manager updates the SQL Server driver packages to the following versions:

- Microsoft ODBC Driver for SQL Server: **18.6.2.1**
- Microsoft OLE DB Driver for SQL Server: **19.4.2.0**

Important

Microsoft ODBC Driver for SQL Server version **18.7.1.1** has a known issue with Configuration Manager version 2603 and earlier that can block site configuration. If you're updating from one of these versions, don't install ODBC driver version 18.7.1.1 before the update. Complete the Configuration Manager update to version 2609 before you install this ODBC driver version.

Configuration Manager automatically installs Microsoft OLE DB Driver for SQL Server on site servers and on computers that host the SMS Provider or a management point. The SQL Server Native Client (`sqlncli.msi`) dependency is removed from all Configuration Manager components and site roles.

For ODBC installation requirements and version guidance, see [ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server). For automatic OLE DB driver installation on applicable roles, see [Site and site system prerequisites](../configs/site-and-site-system-prerequisites).

### .NET Framework applications upgraded to version 4.7.2

All Configuration Manager C# applications that previously targeted .NET Framework 4.6.2 now target .NET Framework 4.7.2.

### Microsoft Visual C++ Redistributable updated

Configuration Manager updates Microsoft Visual C++ Redistributable to version 14.51.36247.

## Cloud management gateway

### Shared key access automatically disabled for CMG storage

Shared key access is automatically disabled for cloud management gateway (CMG) storage, even if you haven't previously selected the option to disable it in the console.

### CMG virtual machine scale set image uses Windows Server 2022

Cloud management gateway (CMG) virtual machine scale sets use a supported Windows Server 2022 image offer that doesn't include the deprecated .NET 6 packages. For more information, see [KB 37942646](../../../hotfix/2603/37942646).

### CMG deployments use Azure Load Balancer inbound NAT rules version 2

When you update to version 2609, CMG deployments are automatically migrated from Azure Load Balancer inbound NAT rules version 1 to version 2. Azure Load Balancer inbound NAT rules version 1 retire on September 30, 2027. Install version 2609 before the retirement date to ensure that CMG deployments use the supported inbound NAT rule version.

For more information, see [Migrate NAT pools to NAT rules](/en-us/azure/load-balancer/load-balancer-nat-pool-migration?tabs=azure-cli).

### New cloud management gateway virtual machine sizes

Cloud management gateway (CMG) virtual machine scale sets use new VM sizes. The previously used Av2-series and B-series (V1) VM sizes are scheduled to retire in November 2028 and already have limited capacity in some Azure regions.

When you update to version 2609, existing CMG deployments are automatically migrated to the corresponding new VM size. The new VM sizes provide higher performance and more memory at a price that's generally close to the previous sizes.

Important

Upgrade the Configuration Manager console after updating to version 2609. The updated console is required to display the new CMG VM sizes correctly.

| CMG tier | Previous VM size | Previous vCPU | Previous memory | New VM size | New vCPU | New memory |
| --- | --- | --- | --- | --- | --- | --- |
| Small | Standard\_B2s | 2 | 4 GiB | Standard\_D2ads\_v6 | 2 | 8 GiB |
| Medium | Standard\_A2\_v2 | 2 | 4 GiB | Standard\_D4ads\_v6 | 4 | 16 GiB |
| Large | Standard\_A4\_v2 | 4 | 16 GiB | Standard\_D8ads\_v6 | 8 | 32 GiB |

Retirement dates are subject to change. For the current retirement date and other VM series retirement details, see [Retired Azure VM size series](/en-us/azure/virtual-machines/sizes/lifecycle/retired-sizes-list). VM pricing varies by region. For current pricing, see [Azure Virtual Machines pricing](https://azure.microsoft.com/pricing/details/virtual-machines/windows/).

## Asset Intelligence

### Asset Intelligence reports removed

Asset Intelligence reports are removed from the **Monitoring &gt; Reporting &gt; Reports** node.

### Asset Intelligence home page updated

The **Catalog Synchronization** and **Inventoried Software Status** sections are removed from the Asset Intelligence home page. The page now displays deprecation information and links to the product lifecycle dashboard and Asset Intelligence client WMI classes.