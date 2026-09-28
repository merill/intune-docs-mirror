---
layout: Conceptual
title: Paths to co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-paths
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
description: Understand the prerequisites for the two primary ways for you to setup co-management.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: e238f564-289b-1df1-70a9-b0a9e482e0bf
document_version_independent_id: 917de60a-292a-6a3b-a6da-8875dae3f100
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-paths.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-paths
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-paths.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 06c2327b-6e16-87eb-667d-2c9d7a0a02ea
---

# Paths to co-management - Configuration Manager | Microsoft Learn

There are two primary ways for you to set up co-management. It's important to understand the prerequisites for each path. They each require some combination of Microsoft Entra ID, Configuration Manager, Microsoft Intune, and Windows 10 or later.

1. Auto-enroll existing Configuration Manager-managed devices into Intune
2. Bootstrap the Configuration Manager client with modern provisioning

Tip

As we talk with our customers that are using Microsoft Intune to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and Microsoft Entra hybrid joined devices. Many customers confuse these two topics – the first is a management option, while the second is an identity option. See the blog post [Understanding hybrid Microsoft Entra ID and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog aims to clarify Microsoft Entra hybrid join and co-management, how they work together but are not the same thing.

## Path 1: Auto-enroll existing clients

Taking this path can get your existing Configuration Manager-managed devices quickly enrolled into Intune. The management of these devices from Configuration Manager is no different from before you enable co-management. Now you get all the cloud-based benefits. This path is transparent to your users.

Here's what you need to set it up:

- Hybrid Microsoft Entra ID
    - One of the following [Microsoft Entra hybrid identity options](/en-us/azure/active-directory/hybrid/plan-connect-user-signin):
        - [Password hash synchronization](/en-us/azure/active-directory/hybrid/plan-connect-user-signin#password-hash-synchronization) with [Seamless Single Sign-on (SSO)](/en-us/azure/active-directory/hybrid/how-to-connect-sso)
        - [Pass-through authentication](/en-us/azure/active-directory/hybrid/how-to-connect-pta) with [Seamless Single Sign-on (SSO)](/en-us/azure/active-directory/hybrid/how-to-connect-sso)
        - [Federated SSO (with Active Directory Federation Services (AD FS))](/en-us/azure/active-directory/hybrid/plan-connect-user-signin#federation-that-uses-a-new-or-existing-farm-with-ad-fs-in-windows-server-2012-r2)
    - Microsoft Entra Connect
    - Microsoft Entra ID P1 or P2 license
    - Configure Microsoft Entra hybrid join (choose one option):
        - For managed domains
        - For federated domains
- Client agent setting for Microsoft Entra hybrid join
- Configure auto-enrollment of devices to Intune
- Enable co-management in Configuration Manager

For a tutorial on this path, see [Tutorial: Enable co-management for existing Configuration Manager clients](tutorial-co-manage-clients).

## Path 2: Bootstrap with modern provisioning

This path is for those devices that are first enrolled with Intune. They are cloud-first devices and use Intune to install the Configuration Manager client.

Here's what you need to set it up:

1. [Setup enhanced HTTP](../core/plan-design/hierarchy/enhanced-http)
2. [Create the cloud services in Azure](../core/servers/deploy/configure/azure-services-wizard)
3. [Configure the management point and clients to use the cloud management gateway](../core/clients/manage/cmg/setup-cloud-management-gateway)
4. [Use Intune to deploy the Configuration Manager client](how-to-prepare-win10)

For a tutorial on this path, see [Tutorial: Enable co-management for new internet-based devices](tutorial-co-manage-new-devices).