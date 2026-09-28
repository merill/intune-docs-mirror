---
layout: Conceptual
title: Introduction to the LTSB - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/introduction-to-the-ltsb
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
description: Learn about the long-term servicing branch of Configuration Manager.
ms.date: 2019-08-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 11bfcd39-a82f-15b5-a26b-4b98848304b9
document_version_independent_id: 37a96a6b-c593-c0fd-e268-451ced750a0c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/introduction-to-the-ltsb.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/introduction-to-the-ltsb
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/introduction-to-the-ltsb.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 0be0be5b-20eb-77f9-e549-fa971f927525
---

# Introduction to the LTSB - Configuration Manager | Microsoft Learn

*Applies to: System Center Configuration Manager (Long-Term Servicing Branch)*

The long-term servicing branch (LTSB) of Configuration Manager is a distinct branch that's designed as an install option available to all customers. However, it's the only option for customers who let lapse their Software Assurance (SA) or equivalent subscription rights for Configuration Manager.

Based on Configuration Manager version 1606, the LTSB has reduced functionality when compared to the current branch of Configuration Manager.

In some cases, the support lifecycle of a dependent component may end before the end of support for the Configuration Manager LTSB itself. In such scenarios, Configuration Manager LTSB continues to be supported through its defined end of support, provided that the reported issue is not caused by the out-of-support dependent component.

Tip

The Configuration Manager LTSB isn't related to the System Center suite long-term servicing channel (LTSC). For more information, see [Overview of System Center release options](/en-us/system-center/ltsc-and-sac-overview).

## Features that aren't available

The current branch of Configuration Manager supports the following functionality that isn't available when you use the LTSB:

- In-console updates that add new features and improvements.
- Support for newly released operating systems to use as site servers and clients.
- On-premises MDM
- The Windows servicing dashboard and servicing plans, including support for recent Windows versions.
- Support for future releases of Windows Server and Windows 10 LTSB
- Asset Intelligence
- Cloud-based distribution points
- Exchange Online as an Exchange Connector

Although support for these features isn't available with the LTSB, some features remain visible in the Configuration Manager console, but can't be selected or used.

Cloud integrations, as well as any features included with Configuration Manager current branch version 1610 or later, aren't available to the LTSB. These features include, but aren't limited to the following:

- Co-management
- Cloud management gateway
- Microsoft Entra integration
- Apps from the Microsoft Store for Business

## Find LTSB documentation

The LTSB is based on current branch version 1606. Use the [current branch documentation](../../), with caveats and limitations that are specific to the LTSB. Those caveats and limitations are identified in the following articles:

- [Install the LTSB](install-the-ltsb)
- [Upgrade the LTSB to the current branch](convert-to-current-branch)
- [Supported configurations for the LTSB](supported-configurations-for-ltsb)
- [Manage the LTSB of Configuration Manager](manage-the-ltsb)

When you reference current branch documentation for the LTSB, details that apply to version 1606 or earlier also apply to the LTSB. Features or details that are introduced with version 1610 or later aren't supported by the LTSB.

## Licensing overview for the LTSB

Customers with active Software Assurance (SA) on Configuration Manager licenses, or with equivalent subscription rights as of October 1, 2016, have rights to use the October 2016 version 1606 release of Configuration Manager. Customers with rights to Configuration Manager on or after October 1, 2016, will find two licensed options upon installation: current branch and long-term servicing branch (LTSB).

Customers that have perpetual rights to System Center Configuration Manager, or that allow SA or subscription to lapse after October 1, can install the version of System Center Configuration Manager LTSB that is current at the time of lapse.

For more information about these licenses, see the [Complete terms and conditions for the products you purchase through Microsoft Volume Licensing programs](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?mode=1).

For more information about licensing for Configuration Manager branches, see [Configuration Manager licensing and branches](learn-more-editions).