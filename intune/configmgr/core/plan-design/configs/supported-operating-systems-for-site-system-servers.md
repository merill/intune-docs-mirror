---
layout: Conceptual
title: Supported site system servers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers
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
description: Learn which Windows versions you can use to host a Configuration Manager site or site system role.
ms.date: 2024-12-19T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: de76fdfb-135a-5123-4e1c-4cd1d7f84221
document_version_independent_id: cb2e2472-e098-1977-33f4-2eb5674e681f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: 318b0785-bc3a-ef61-2c05-3cc14b1f037d
---

# Supported site system servers - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article details the Windows versions that you can use to host a Configuration Manager site or site system role.

## Windows Server 2025

*Applies to Datacenter: Azure Edition, Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point ^Note 1^
- Endpoint Protection point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server ^Note 2^
- SMS Provider
- Software update point
- State migration point

## Windows Server 2022

*Applies to Datacenter: Azure Edition, Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Asset Intelligence synchronization point
- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point ^Note 1^
- Endpoint Protection point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server ^Note 2^
- SMS Provider
- Software update point
- State migration point

## Windows Server 2019

*Applies to Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Asset Intelligence synchronization point
- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point ^Note 1^
- Endpoint Protection point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server ^Note 2^
- SMS Provider
- Software update point
- State migration point

## Windows Server 2016

*Applies to Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Asset Intelligence synchronization point
- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point ^Note 1^
- Endpoint Protection point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server ^Note 2^
- SMS Provider
- Software update point
- State migration point

## Windows Storage Server 2016

Site system server:

- Distribution point ^Note 1^

## Windows Server 2012/2012 R2

*Applies to Standard and Datacenter*

On October 10th, 2023, Windows Server 2012 and Windows Server 2012 R2 entered the Extended Support Updates phase. Microsoft will no longer provide support for Configuration Manager site servers or roles installed to these Operating Systems. For more information, see [Extended Security Updates and Configuration Manager](supported-operating-systems-for-clients-and-devices#bkmk_ESU).

Tip

Starting in Configuration Manager 2309, you'll be notified when performing a site upgrade about site systems with operating systems that are past the end of support date.

Starting in Configuration Manager 2403 you'll be blocked from performing a site upgrade if any site systems are detected with operating systems that are past the end of support date. For more information, see [Extended Security Updates and Configuration Manager](supported-operating-systems-for-clients-and-devices#bkmk_ESU).

## Client OS versions

The following client OS versions are supported for use as a **distribution point**^Note 1^:

- Windows 11

    For more information on supported build versions and editions, see [Support for Windows 11](support-for-windows-11).
- Windows 10 (x86, x64)

    For more information on supported build versions and editions, see [Support for Windows 10](support-for-windows-10).

This support has the following limitation:

- Distribution points on this OS don't support PXE or multicast with the default Windows Deployment Services. You can PXE-enable a distribution point on this OS with the option to **Enable a PXE responder without Windows Deployment Service**. For more information, see [Install and configure distribution points](../../servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe).

## Server core installations

The server core installation of the following server OS versions is supported for use as a **distribution point**:

- Windows Server 2025
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1809
- Windows Server, version 1803
- Windows Server, version 1709
- Windows Server 2016

This support has the following limitation:

- Distribution points on this OS don't support PXE or multicast with the default Windows Deployment Services. You can PXE-enable a distribution point on this OS with the option to **Enable a PXE responder without Windows Deployment Service**. For more information, see [Install and configure distribution points](../../servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe).

## General notes

### Extended Security Updates for Windows Server 2012 and Windows Server 2012 R2

On October 10th, 2023, Windows Server 2012 and Windows Server 2012 R2 will enter the Extended Support Updates phase. Microsoft will no longer provide support for Configuration Manager site servers or roles installed to these Operating Systems. For more information, see [Extended Security Updates and Configuration Manager](supported-operating-systems-for-clients-and-devices#bkmk_ESU).

### Note 1: Distribution points

Distribution points support several different configurations that each have different requirements. In some cases, these configurations support installation not only on servers, but on client operating systems. For more information, see [Manage content and content infrastructure](../../servers/deploy/configure/manage-content-and-content-infrastructure).

### Note 2: Site database servers

Site database servers aren't supported on a read-only domain controller (RODC). For more information, see [SQL Server security considerations: Installing SQL Server on a domain controller](/en-us/sql/sql-server/install/security-considerations-for-a-sql-server-installation#Install_DC).

Additionally, secondary site servers aren't supported on any domain controller.