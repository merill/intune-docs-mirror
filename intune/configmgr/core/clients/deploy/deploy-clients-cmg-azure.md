---
layout: Conceptual
title: Install the client with Microsoft Entra ID - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-cmg-azure
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
description: Install and assign the Configuration Manager client on Windows devices using Microsoft Entra ID for authentication
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 537cf5a4-8072-7332-e579-35394ecda457
document_version_independent_id: 03ec8ffa-d42c-f3d6-cedb-0deedc6606ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/deploy-clients-cmg-azure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/deploy-clients-cmg-azure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/deploy-clients-cmg-azure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: e1752b02-d940-731e-0742-93c632942a11
---

# Install the client with Microsoft Entra ID - Configuration Manager | Microsoft Learn

To install the Configuration Manager client on Windows devices using Microsoft Entra authentication, integrate Configuration Manager with Microsoft Entra ID. Clients can be on the intranet communicating directly with an HTTPS-enabled management point or any management point in a site enabled for Enhanced HTTP. They can also be internet-based communicating through the CMG or with an Internet-based management point. This process uses Microsoft Entra ID to authenticate clients to the Configuration Manager site. Microsoft Entra ID replaces the need to configure and use client authentication certificates.

Setting up Microsoft Entra ID may be easier for some customers than setting up a public key infrastructure for certificate-based authentication. There are features that require you onboard the site to Microsoft Entra ID, but don't necessarily require the clients to be Microsoft Entra joined. For more information, see the following articles:

- [Plan for Microsoft Entra ID](../../plan-design/security/plan-for-security#azure-active-directory)
- [Use Microsoft Entra ID for co-management](../../../comanage/quickstart-hybrid-aad)

## Before you begin

- A Microsoft Entra tenant is a prerequisite
- Device requirements:

    - A supported version of Windows 10 or later
    - Joined to Microsoft Entra ID, either pure cloud domain-joined, or Microsoft Entra hybrid joined
- User requirements:

    - The signed in user must be a Microsoft Entra identity.
    - If the user is a federated or synchronized identity, configure both Configuration Manager [Active Directory user discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) and [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc). For more information about hybrid identities, see [Define a hybrid identity adoption strategy](/en-us/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-identity-adoption-strategy).
- In addition to the [existing prerequisites](../../plan-design/configs/site-and-site-system-prerequisites#management-point) for the management point site system role, also enable **ASP.NET 4.5** on this server. Include any other options that are automatically selected when enabling ASP.NET 4.5.
- Determine whether your management point needs HTTPS. For more information, see [Enable management point for HTTPS](../manage/cmg/configure-authentication#enable-management-point-for-https).
- Optionally set up a [cloud management gateway](../manage/cmg/overview) (CMG) to deploy internet-based clients. For on-premises clients that authenticate with Microsoft Entra ID, you don't need a CMG.

Important

Use of the NLM AllowedTlsAuthenticationEndpoints Intune Policy can cause Entra-only joined devices to fail to register when on a local network with connectivity to the endpoints specified in the policy.

Tip

Configuration Manager extends its support for internet-based devices that don't often connect to the internal network, aren't able to join Microsoft Entra ID, and don't have a method to install a PKI-issued certificate. For more information, see [Token-based authentication for CMG](deploy-clients-cmg-token).

## Configure Azure Services for Cloud Management

Connect your Configuration Manager site to Microsoft Entra ID as the first step. For details of this process, see [Configure Azure services](../../servers/deploy/configure/azure-services-wizard). Create a connection to the **Cloud Management** service.

Enable [Microsoft Entra user Discovery](../../servers/deploy/configure/configure-discovery-methods#azureaadisc) as part of onboarding to **Cloud Management**.

After you complete these actions, your Configuration Manager site is connected to Microsoft Entra ID.

Note

If your devices are in a Microsoft Entra tenant that's separate from the tenant with a subscription for the CMG compute resources, starting in version 2010 you can disable authentication for tenants not associated with users and devices. For more information, see [Configure Azure services](../../servers/deploy/configure/azure-services-wizard#disable-authentication).

## Configure client settings

These client settings help configure Windows devices to be hybrid-joined. They also enable internet-based clients to use the CMG.

1. Configure the following client settings in the **Cloud Services** group. For more information, see [How to configure client settings](configure-client-settings).

    - **Allow access to cloud distribution point**: Enable this setting to help internet-based devices get the required content to install the Configuration Manager client. Devices can get the content from the CMG.
    - **Automatically register new Windows 10 or later domain joined devices with Microsoft Entra ID**: Set to **Yes** or **No**. The default setting is **Yes**. This behavior is also the default in Windows.

        Tip

        Hybrid-joined devices are joined to an on-premises Active Directory domain and registered with Microsoft Entra ID. For more information, see [Microsoft Entra hybrid joined devices](/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid).
    - **Enable clients to use a cloud management gateway**: Set to **Yes** (default), or **No**.
2. Deploy the client settings to the required collection of devices. Don't deploy these settings to user collections.

To confirm the device is hybrid-joined, run `dsregcmd.exe /status` in a command prompt. If the device is Microsoft Entra joined or hybrid-joined, the **AzureAdjoined** field in the results shows **YES**. For more information, see [dsregcmd command - device state](/en-us/azure/active-directory/devices/troubleshoot-device-dsregcmd).

## Install and register the client using Microsoft Entra identity

To manually install the client using Microsoft Entra identity, first review the general process on [How to install clients manually](deploy-clients-to-windows-computers#BKMK_Manual).

Note

The device needs access to the internet to contact Microsoft Entra ID, but doesn't need to be internet-based.

The following example shows the general structure of the command line: `ccmsetup.exe /mp:<source management point> CCMHOSTNAME=<internet-based management point> SMSSITECODE=<site code> SMSMP=<initial management point> AADTENANTID=<Azure AD tenant identifier> AADCLIENTAPPID=<Azure AD client app identifier> AADRESOURCEURI=<Azure AD server app identifier>`

For more information, see [Client installation properties](about-client-installation-properties).

The `/mp` parameter and `CCMHOSTNAME` property specify one of the following, depending upon the scenario:

- On-premises management point. Only specify the `/mp` parameter. The `CCMHOSTNAME` property isn't required.
- Cloud management gateway
- Internet-based management point

This example uses a cloud management gateway. It replaces sample values: `ccmsetup.exe /mp:https://CONTOSO.EASTUS.CLOUDAPP.AZURE.COM/CCM_Proxy_MutualAuth/72186325152220500 CCMHOSTNAME=CONTOSO.EASTUS.CLOUDAPP.AZURE.COM/CCM_Proxy_MutualAuth/72186325152220500 SMSSITECODE=ABC`

The site publishes additional Microsoft Entra information to the cloud management gateway (CMG). A Microsoft Entra joined client gets this information from the CMG during the ccmsetup process, using the same tenant to which it's joined. This behavior further simplifies installing the client in an environment with more than one Microsoft Entra tenant. The only two required ccmsetup properties are `CCMHOSTNAME` and `SMSSITECODE`.

To automate the client install using Microsoft Entra identity via Microsoft Intune, see [How to prepare internet-based devices for co-management](../../../comanage/how-to-prepare-win10#install-the-configuration-manager-client).