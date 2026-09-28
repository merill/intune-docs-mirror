---
layout: Conceptual
title: Prerequisites to deploy user-available apps - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/prerequisites-deploy-user-available-apps
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
description: When you deploy apps as Available to user collections, there are other requirements for some types of clients.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: a2a2c700-0bea-521d-ce8e-25404ce6a8bd
document_version_independent_id: 29475b33-2b3b-0cb1-54d4-62a340cda4d2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/plan-design/prerequisites-deploy-user-available-apps.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/plan-design/prerequisites-deploy-user-available-apps
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/plan-design/prerequisites-deploy-user-available-apps.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: eb127779-020d-bcea-0695-6afa1cb2d22f
---

# Prerequisites to deploy user-available apps - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you deploy applications as **Available** to user collections, then users can browse Software Center and install the apps they need.

For on-premises domain-joined clients, Software Center uses the user's domain credentials to get the list of available applications from the management point.

There are other requirements for clients that are internet-based, joined to Microsoft Entra ID, or both.

## Microsoft Entra joined devices

If you deploy applications as available to users, they can browse and install them through Software Center on Microsoft Entra devices. Configure the following prerequisites to enable this scenario:

- Enable HTTPS on the management point or enable Enhanced HTTP on the site.
- Integrate the site with [Microsoft Entra ID](../../core/servers/deploy/configure/azure-services-wizard) for **Cloud Management**.

    - Configure [Microsoft Entra user Discovery](../../core/servers/deploy/configure/configure-discovery-methods#azureaadisc).
- Deploy an application as available to a collection of users from Microsoft Entra ID.
- Enable the client setting **Use new Software Center** in the [Computer agent](../../core/clients/deploy/about-client-settings#computer-agent) group.
- The client OS must be Windows 10 or later, and joined to Microsoft Entra ID. Either as purely cloud domain-joined, or Microsoft Entra hybrid joined.
- To support internet-based clients:

    - Deploy a [cloud management gateway](../../core/clients/manage/cmg/overview) (CMG).
    - Distribute any application content to a content-enabled CMG.
    - Enable the client setting: **Enable user policy requests from Internet clients** in the [Client Policy](../../core/clients/deploy/about-client-settings#client-policy) group.
- To support clients on the intranet:

    - Add the content-enabled CMG to a boundary group used by the clients.
    - Clients must resolve the fully qualified domain name (FQDN) of the management point.

    Note

    For a client detected as on the intranet, but communicating via the cloud management gateway (CMG), it uses Microsoft Entra identity for devices joined to Microsoft Entra ID. These devices can be cloud-joined or hybrid-joined.

## Internet-based domain-joined devices

An internet-based, domain-joined device that isn't joined to Microsoft Entra ID and communicates via a cloud management gateway (CMG) can get apps deployed as available. The Active Directory domain user of the device needs a matching Microsoft Entra identity. When the user starts Software Center, Windows prompts them to enter their Microsoft Entra credentials. They can then see any available apps.

Configure the following prerequisites to enable this functionality:

- Windows 10 or later device, and:

    - Joined to your on-premises Active Directory domain.
    - Can communicate via [CMG](../../core/clients/manage/cmg/plan-cloud-management-gateway).
- The site has discovered the user by *both*[Active Directory](../../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) and [Microsoft Entra user discovery](../../core/servers/deploy/configure/about-discovery-methods#azureaddisc).

Note

If you apply a [software restriction policy](/en-us/windows-server/identity/software-restriction-policies/administer-software-restriction-policies) to the device, it can block the authentication prompt in Windows. Review any domain or local group policies that you apply to the device. Then remove any that might interfere with this Software Center behavior.