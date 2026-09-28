---
layout: Conceptual
title: Set up hybrid Microsoft Entra ID - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-setup-hybrid-aad
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
description: If your environment currently has domain-joined Windows devices, set up hybrid Microsoft Entra ID before you enable co-management
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: e049675e-6a8d-c715-85ac-8719eb810fe8
document_version_independent_id: a86a5a8d-8fcd-b4dc-cae2-d9a9f83f5392
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-setup-hybrid-aad.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-setup-hybrid-aad
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-setup-hybrid-aad.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 1fc5b6cd-539a-9e49-f718-7b2d47b5a1c9
---

# Set up hybrid Microsoft Entra ID - Configuration Manager | Microsoft Learn

If you have Windows 10 or later devices joined to on-premises Active Directory, before you enable co-management in Configuration Manager, first join these devices to Microsoft Entra ID. This process is called Microsoft Entra hybrid join.

In the following video, senior program manager Sandeep Deo and product marketing manager Adam Harbour discuss and demo configuring devices in Microsoft Entra ID:

The Microsoft Entra hybrid join process automatically registers your on-premises domain-joined devices with Microsoft Entra ID. For more information on this process, see the following articles:

- [What is a device identity in Microsoft Entra ID?](/en-us/azure/active-directory/devices/overview)
- [How to plan your Microsoft Entra hybrid join](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan)

Microsoft Entra hybrid join is one of the key foundations for co-management. This process can be challenging for some customers, for example:

- Your organization uses a third-party identity solution
- The complexities of setting up Active Directory Federation Services (ADFS)

Resolving these challenges can take some guidance. This article helps to mitigate any delays.

Tip

As we talk with our customers that are using Microsoft Intune to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and Microsoft Entra hybrid joined devices. Many customers confuse these two topics. Co-management is a management option, while Microsoft Entra ID is an identity option. For more information, see [Understanding hybrid Microsoft Entra ID and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog post aims to clarify Microsoft Entra hybrid join and co-management, how they work together, but aren't the same thing.

## How to do it

Devices are similar to users when creating an identity that you want to protect. To protect a device's identity at any time and in any location, you need to bring the identity of that device into Microsoft Entra ID.

Based on the type of domain you're using, there are two primary ways to do that. Configure Microsoft Entra hybrid join for one of the following domain types:

- [Federated domains](/en-us/azure/active-directory/devices/hybrid-azuread-join-federated-domains)
- [Managed domains](/en-us/azure/active-directory/devices/hybrid-azuread-join-managed-domains)

The two preceding methods provide the best experience. For more detailed information including the fully manual process, see the following articles:

- [How to plan your Microsoft Entra hybrid join implementation](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan)
- [ADFS pass-through authentication for hybrid Microsoft Entra ID](/en-us/windows-server/identity/ad-fs/ad-fs-overview), which includes Microsoft Entra discovery

For troubleshooting guidance, see the [Microsoft Entra hybrid join troubleshooting guide](/en-us/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current).

## Case study

A large European software company with over 100,000 users in its network took a granular and phased approach towards enabling Microsoft Entra hybrid join.

During the planning phase, since Microsoft Entra hybrid join is a key element supporting co-management, the Configuration Manager administrators worked with the identity team. This software company had many ADFS rules, and some of them were complex. To address this challenge, the identity team reviewed the existing ADFS rules before they enabled Microsoft Entra hybrid join. The IT team also chose to upgrade Microsoft Entra Connect to the latest version. Microsoft Entra Connect now provides an automated process flow for enabling Microsoft Entra hybrid join.

After successful deployment and testing in their pre-production environment, this customer enabled Microsoft Entra hybrid join for the whole production estate. Within a week, they had every Windows 10 device co-managed.

## Contact FastTrack

If you need assistance setting up Microsoft Entra ID at any point in the process, go to [Microsoft FastTrack](https://microsoft.com/fasttrack/), sign in, and request assistance.

For more information, see [Get help from FastTrack](quickstart-fasttrack).