---
layout: Conceptual
title: Introduction to certificate profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/introduction-to-certificate-profiles
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
description: Learn how certificate profiles in Configuration Manager work with Active Directory Certificate Services.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 4c08a14a-7d06-8cda-f780-94a49afac5c9
document_version_independent_id: 96c9e5cc-6b6b-c04b-313a-e0e4e6437629
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/introduction-to-certificate-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/introduction-to-certificate-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/introduction-to-certificate-profiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 8c0127f2-0b3c-2274-eb96-b6f5e7eb7136
---

# Introduction to certificate profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

Certificate profiles work with Active Directory Certificate Services and the Network Device Enrollment Service (NDES) role. Create and deploy authentication certificates for managed devices so that users can easily access organizational resources. For example, you can create and deploy certificate profiles to provide the necessary certificates for users to connect to VPN and wireless connections.

Certificate profiles can automatically configure user devices for access to organizational resources such as Wi-Fi networks and VPN servers. Users can access these resources without manually installing certificates or using an out-of-band process. Certificate profiles help to secure resources because you can use more secure settings that are supported by your public key infrastructure (PKI). For example, require server authentication for all Wi-Fi and VPN connections because you've deployed the required certificates on the managed devices.

Certificate profiles provide the following management capabilities:

- Certificate enrollment and renewal from a certification authority (CA) for devices that run different OS types and versions. These certificates can then be used for Wi-Fi and VPN connections.
- Deployment of trusted root CA certificates and intermediate CA certificates. These certificates configure a chain of trust on devices for VPN and Wi-Fi connections when server authentication is required.
- Monitor and report about the installed certificates.

**Example 1**: All employees need to connect to Wi-Fi hotspots in multiple office locations. To enable easy user connection, first deploy the certificates needed to connect to Wi-Fi. Then deploy Wi-Fi profiles that reference the certificate.

**Example 2**: You have a PKI in place. You want to move to a more flexible, secure method of deploying certificates. Users need to access organizational resources from their personal devices without compromising security. Configure certificate profiles with settings and protocols that are supported for the specific device platform. The devices can then automatically request these certificates from an internet-facing enrollment server. Then, configure VPN profiles to use these certificates so that the device can access organizational resources.

## Types

There are three types of certificate profiles:

- **Trusted CA certificate**: Deploy a trusted root CA or intermediate CA certificate. These certificates form a chain of trust when the device must authenticate a server.
- **Simple Certificate Enrollment Protocol (SCEP)**: Request a certificate for a device or user by using the SCEP protocol. This type requires the Network Device Enrollment Service (NDES) role on a server running Windows Server 2012 R2 or later.

    To create a **Simple Certificate Enrollment Protocol (SCEP)** certificate profile, first create a **Trusted CA certificate** profile.
- **Personal information exchange (.pfx)**: Request a .pfx (also known as PKCS #12) certificate for a device or user. There are two methods to create PFX certificate profiles:

    - [Import credentials](../../mdm/deploy-use/import-pfx-certificate-profiles) from existing certificates
    - [Define a certificate](../../mdm/deploy-use/create-pfx-certificate-profiles) authority to process requests

    Note

    Configuration Manager doesn't enable this optional feature by default. You must enable this feature before using it. For more information, see [Enable optional features from updates](../../core/servers/manage/optional-features).

    You can use Microsoft or Entrust as certificate authorities for **Personal information exchange (.pfx)** certificates.

## Requirements

To deploy certificate profiles that use SCEP, install the certificate registration point on a site system server. Also install a policy module for NDES, the Configuration Manager Policy Module, on a server that runs Windows Server 2012 R2 or later. This server requires the Active Directory Certificate Services role. It also requires a working NDES that's accessible to the devices that require the certificates. If your devices need to enroll for certificates from the internet, then your NDES server must be accessible from the internet. For example, to safely enable traffic to the NDES server from the internet, you can use [Azure Application Proxy](/en-us/entra/identity/app-proxy/).

PFX certificates also require a certificate registration point. Also specify the certificate authority (CA) for the certificate and the relevant access credentials. You can specify either Microsoft or Entrust as certificate authorities.

For more information about how NDES supports a policy module so that Configuration Manager can deploy certificates, see [Using a Policy Module with the Network Device Enrollment Service](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn473016%28v=ws.11%29).

Depending on the requirements, Configuration Manager supports deploying certificates to different certificate stores on various device types and operating systems. The following devices and operating systems are supported:

- Windows 10
- Windows 10 Mobile
- Windows 8.1
- Windows Phone 8.1

Note

Use Configuration Manager on-premises MDM to manage Windows Phone 8.1 and Windows 10 Mobile. For more information, see [On-premises MDM](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure).

A typical scenario for Configuration Manager is to install trusted root CA certificates to authenticate Wi-Fi and VPN servers. Typical connections use the following protocols:

- Authentication protocols: EAP-TLS, EAP-TTLS, and PEAP
- VPN tunneling protocols: IKEv2, L2TP/IPsec, and Cisco IPsec

An enterprise root CA certificate must be installed on the device before the device can request certificates by using a SCEP certificate profile.

You can specify settings in a SCEP certificate profile to request customized certificates for different environments or connectivity requirements. The **Create Certificate Profile Wizard** has two pages for enrollment parameters. The first, **SCEP Enrollment**, includes settings for the enrollment request and where to install the certificate. The second, **Certificate Properties**, describes the requested certificate itself.

## Deploy

When you deploy a SCEP certificate profile, the Configuration Manager client processes the policy. It then requests a SCEP challenge password from the management point. The device creates a public/private key pair, and generates a certificate signing request (CSR). It sends this request to the NDES server. The NDES server forwards the request to the certificate registration point site system via the NDES policy module. The certificate registration point validates the request, checks the SCEP challenge password, and verifies that the request wasn't tampered with. It then approves or denies the request. If approved, the NDES server sends the signing request to the connected certificate authority (CA) for signing. The CA signs the request, and then it returns the certificate to the requesting device.

Deploy certificate profiles to user or device collections. You can specify the destination store for each certificate. Applicability rules determine whether the device can install the certificate.

When you deploy a certificate profile to a user collection, [user device affinity](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity) determines which of the users' devices install the certificates. When you deploy a certificate profile with a user certificate to a device collection, by default each of the users' primary devices install the certificates. To install the certificate on any of the users' devices, change this behavior on the **SCEP Enrollment** page of the **Create Certificate Profile Wizard**. If the devices are in a workgroup, Configuration Manager doesn't deploy user certificates.

## Monitor

You can monitor certificate profile deployments by viewing compliance results or reports. For more information, see [How to monitor certificate profiles](monitor-certificate-profiles).

## Automatic revocation

Configuration Manager automatically revokes user and computer certificates that were deployed by using certificate profiles in the following circumstances:

- The device is retired from Configuration Manager management.
- The device is blocked from the Configuration Manager hierarchy.

To revoke the certificates, the site server sends a revocation command to the issuing certification authority. The reason for the revocation is **Cease of Operation**.

Note

To properly revoke a certificate, the computer account for the top-level site in the hierarchy needs the permission to **issue and manage certificates** on the CA.

For improved security, you can also restrict CA managers on the CA. Then only give this account permissions on the specific certificate template that you use for the SCEP profiles on the site.