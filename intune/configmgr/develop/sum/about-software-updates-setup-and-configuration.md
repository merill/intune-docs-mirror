---
layout: Conceptual
title: Software Updates Setup and Configuration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-setup-and-configuration
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
description: Before software update compliance assessment data is displayed in the Configuration Manager console and before software updates can be deployed to client computers, you must install and configure a software update point.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 03b399fc-33de-9e50-9749-e10ba825e525
document_version_independent_id: 5d9dc58f-7d50-e3a2-423c-597ec26170eb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/about-software-updates-setup-and-configuration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/about-software-updates-setup-and-configuration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/about-software-updates-setup-and-configuration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 34019284-61e3-a865-cfcf-9c7eaad9ff5a
---

# Software Updates Setup and Configuration - Configuration Manager | Microsoft Learn

Before software update compliance assessment data is displayed in the Configuration Manager console and before software updates can be deployed to client computers, you must install and configure a software update point. In addition, consider the configuration and settings for other software updates components, such as the Windows Server Update Services (WSUS) server and the software updates client agent. For more information, see [Windows Server Update Services](/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).

For more information about software updates, see [Deploy and manage software updates](../../sum/understand/software-updates-introduction).

## Software Update Point

A software update point in Configuration Manager is a required component of software updates, and after it is installed, the software update point is displayed as a site system role in the Configuration Manager console. The software update point site system role must be created on a site system server that has Windows Server Update Services (WSUS) 3.0 installed.

## WSUS Server and SSL

When a Configuration Manager site server is in native mode, or when the active software update point is configured to use Secure Sockets Layer (SSL), you must configure five virtual roots to use a secured channel on the active software update point server. The virtual roots are located on the Web site that the WSUS server uses, and they are modified by using the Internet Information Services (IIS) Manager. After you have configured the virtual roots, you must run the WSUSUtil tool to let the health monitoring component of WSUS know that it should use SSL.

## Port Settings Used by WSUS

When you create and configure a software update point in Configuration Manager, you must specify the port settings that the WSUS 3.0 server uses.

## Software Updates Client Agent

When the Software Updates Client Agent is enabled in Configuration Manager, it sends a policy to the client computers that are assigned to the site. This policy requests that the software updates components be enabled. The Software Updates Client Agent components work together to perform compliance assessment scans, install software updates at their configured deadline or when they are manually initiated, and reevaluate whether previously installed software updates are still installed, and if not, install them again. The Software Updates Client Agent properties are site-wide client settings.