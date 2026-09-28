---
layout: Conceptual
title: Microsoft Intune tenant attach prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/prerequisites
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
description: Prerequisites for Microsoft Intune tenant attach.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: article
ms.subservice: core-infra
ms.collection: tier3
ms.custom: sfi-ga-nochange
locale: en-us
document_id: 7cd48cfb-8d4a-0eae-a189-94f4b90907b3
document_version_independent_id: 7cd48cfb-8d4a-0eae-a189-94f4b90907b3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/prerequisites.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/prerequisites
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/prerequisites.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 2209c127-c064-a843-65e0-44c78691b7a5
---

# Microsoft Intune tenant attach prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. You can upload your Configuration Manager devices to the cloud service and take actions from the **Devices** page in the admin center. Some of the features you may want to use include:

- Run PowerShell [scripts](scripts)
- Install [applications](applications)
- Query devices with [CMPivot](cmpivot-samples-attached?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json)
- Display a [timeline](timeline) of events from the device

## Prerequisites

- An account that is a **[Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)** for signing in when applying this onboarding change.

    Onboarding creates a third-party app and a first party service principal in your Microsoft Entra tenant.

    Important

    The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../core/understand/fundamentals-of-role-based-administration).
- An Azure cloud environment.

    - The **Upload to Microsoft Endpoint Manager admin center** option is disabled for Microsoft Azure China 21Vianet (Azure China Cloud) and Azure US Government Cloud. Starting in version 2107, this option is available for US Government customers.
- Starting in version 2107, United States Government customers can use the following tenant attach features in the US Government cloud:

    - Account onboarding
    - Tenant sync to Intune
    - Device sync to Intune
    - Device actions in the Microsoft Intune admin center
- The geographic location of the Azure tenant and the service connection point should be the same.
- At least one Intune license for you as the administrator to access the Microsoft Intune admin center.
- The [administration service](../develop/adminservice/overview) in Configuration Manager needs to be set up and functional.
- If your central administration site has a [remote provider](../core/plan-design/hierarchy/plan-for-the-sms-provider), then follow the instructions for the [CAS has a remote provider](../core/servers/manage/cmpivot-changes#cas-has-a-remote-provider) scenario in the CMPivot article.

This feature supports all OS versions that Configuration Manager currently supports as a client. For more information, see [Supported OS versions for clients and devices](../core/plan-design/configs/supported-operating-systems-for-clients-and-devices).

## Permissions

The user accounts performing device actions have the following prerequisites:

- The user account needs to be a synced user object in Microsoft Entra ID (hybrid identity). This means that the user is synced to Microsoft Entra ID from Active Directory.
    - For Configuration Manager version 2103, and later:  Has been discovered with either [Microsoft Entra user discovery](../core/servers/deploy/configure/about-discovery-methods#azureaddisc) or [Active Directory user discovery](../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
- The **Initiate Configuration Manager action** permission under **Remote tasks**in the Microsoft Intune admin center.
    - For more information about adding or verifying permissions in the admin center, see [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview#rbac-roles).

## Internet endpoints

- `https://aka.ms/configmgrgateway`
- `https://*.manage.microsoft.com`*for Azure public cloud customers*
- `https://*.manage.microsoft.us`*for US Government cloud customers on version 2107 or later*
- `https://dc.services.visualstudio.com`

The service connection point makes a long standing outgoing connection to the notification service hosted on `https://*.manage.microsoft.com`. Verify the proxy used for the service connection point doesn't time out outgoing connections too quickly. We recommend 3 minutes for outgoing connections to this internet endpoint. 

If your environment has proxy rules to allow only specific certificate revocation lists (CRLs) or online certificate status protocol (OCSP) verification locations, also allow the following CRL and OCSP URLs:

- `http://crl3.digicert.com`
- `http://crl4.digicert.com`
- `http://ocsp.digicert.com`
- `http://www.d-trust.net`
- `http://root-c3-ca2-2009.ocsp.d-trust.net`
- `http://crl.microsoft.com`
- `http://oneocsp.microsoft.com`
- `http://ocsp.msocsp.com`
- `http://www.microsoft.com/pkiops`

The service connection point validates important internet endpoints for tenant attach. These checks help make sure that the cloud service is available. It also helps you troubleshoot issues by quickly determining if network connectivity is a problem. For more information, see [Validate internet access](../core/servers/deploy/configure/about-the-service-connection-point#validate-internet-access).

Note

The service connection point checks the CRL. If this server doesn't have access to the URLs listed above, the CRL check fails. Consider setting a system proxy or use the following command: 'netsh winhttp set proxy'. For more information, see [How the Windows Update client determines which proxy server to use to connect to the Windows Update Web site](https://support.microsoft.com/topic/how-the-windows-update-client-determines-which-proxy-server-to-use-to-connect-to-the-windows-update-web-site-08612ae5-3722-886c-f1e1-d012516c22a1). Make sure that you include a bypass list for internal site communications. This configuration may be necessary as the proxy server settings within Configuration Manager only configure the proxy for Configuration Manager applications and not the underlying OS.

## Limitations

Currently, Configuration Manager devices aren't included when retrieving a device list through a PowerShell script or through Microsoft Graph API. To work around this issue, use the **Export** option from the **All devices** page in the admin center.