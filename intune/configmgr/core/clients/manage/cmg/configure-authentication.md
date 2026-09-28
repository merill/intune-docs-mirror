---
layout: Conceptual
title: Configure CMG client authentication - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-authentication
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
description: Configure authentication methods for clients to use a cloud management gateway (CMG).
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 487b0a14-24a7-c5dc-9350-cde232264ea0
document_version_independent_id: 61c19523-86f3-e983-6021-cd3a1267f4be
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/configure-authentication.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/configure-authentication
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/configure-authentication.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 72e7b5b7-b40a-e3bb-c938-ecfe7b1c8b8d
---

# Configure CMG client authentication - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The next step in the setup of a cloud management gateway (CMG) is to configure how clients authenticate. Because these clients are potentially connecting to the service from the untrusted public internet, they have a higher authentication requirement. There are three options:

- Microsoft Entra ID
- PKI certificates
- Configuration Manager site-issued tokens

This article describes how to configure each of these options. For more foundational information, see [Plan for CMG client authentication methods](plan-client-authentication).

## Microsoft Entra ID

If your internet-based devices are running Windows 10 or later, use Microsoft Entra modern authentication with the CMG. This authentication method is the only one that enables user-centric scenarios.

This authentication method requires the following configurations:

- The devices need to be either cloud domain-joined or Microsoft Entra hybrid joined, and the user also needs a Microsoft Entra identity.

    Tip

    To check if a device is cloud-joined, run `dsregcmd.exe /status` in a command prompt. If the device is Microsoft Entra joined or hybrid-joined, the **AzureAdjoined** field in the results shows **YES**. For more information, see [dsregcmd command - device state](/en-us/azure/active-directory/devices/troubleshoot-device-dsregcmd).
- One of the primary requirements for using Microsoft Entra authentication for internet-based clients with a CMG is to integrate the site with Microsoft Entra ID. You already completed that action in the [prior step](configure-azure-ad).
- There are a few other requirements, depending upon your environment:

    - Enable user discovery methods for hybrid identities
    - Enable ASP.NET 4.5 on the management point
    - Configure client settings

For more information on these prerequisites, see [Install clients using Microsoft Entra ID](../../deploy/deploy-clients-cmg-azure).

## PKI certificate

Use these steps if you have a public key infrastructure (PKI) that can issue client authentication certificates to devices.

This certificate may be required on the CMG connection point. For more information, see CMG connection point.

### Issue the certificate

Create and issue this certificate from your PKI, which is outside of the context of Configuration Manager. For example, you can use Active Directory Certificate Services and group policy to automatically issue client authentication certificates to domain-joined devices. For more information, see [Example deployment of PKI certificates: Deploy the client certificate](../../../plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).

The CMG client authentication certificate supports the following configurations:

- 2048-bit or 4096-bit key length
- This certificate supports key storage providers for certificate private keys (v3). For more information, see [CNG v3 certificates overview](../../../plan-design/network/cng-certificates-overview).

### Export the client certificate's trusted root

The CMG has to trust the client authentication certificates to establish the HTTPS channel with clients. To accomplish this trust, export the trusted root certificate chain. Then supply these certificates when you create the CMG in the Configuration Manager console.

Make sure to export all certificates in the trust chain. For example, if the client authentication certificate is issued by an intermediate CA, export both the intermediate and root CA certificates.

Note

When clients use either Microsoft Entra ID or tokens for authentication, this certificate isn't required. Export this certificate only when clients are not joined to Entra ID and instead use PKI certificates for authentication.

After you issue a client authentication certificate to a computer, use this process on that computer to export the trusted root certificate.

1. Open the Start menu. Type "run" to open the Run window. Open `mmc`.
2. From the File menu, choose **Add/Remove Snap-in...**.
3. In the Add or Remove Snap-ins dialog box, select **Certificates**, then select **Add**.

    1. In the Certificates snap-in dialog box, select **Computer account**, then select **Next**.
    2. In the Select Computer dialog box, select **Local computer**, then select **Finish**.
    3. In the Add or Remove Snap-ins dialog box, select **OK**.
4. Expand **Certificates**, expand **Personal**, and select **Certificates**.
5. Select a certificate whose Intended Purpose is **Client Authentication**.

    1. From the Action menu, select **Open**.
    2. Go to the **Certification Path** tab.
    3. Select the next certificate up the chain, and select **View Certificate**.
6. On this new Certificate dialog box, go to the **Details** tab. Select **Copy to File...**.
7. Complete the Certificate Export Wizard using the default certificate format, **DER encoded binary X.509 (.CER)**. Make note of the name and location of the exported certificate.
8. Export all of the certificates in the certification path of the original client authentication certificate. Make note of which exported certificates are intermediate CAs, and which ones are trusted root CAs.

### CMG connection point

To securely forward client requests, the CMG connection point requires a secure connection with the management point. If you're using PKI client authentication, and the internet-enabled management point is HTTPS, issue a client authentication certificate to the site system server with the CMG connection point role.

Note

The CMG connection point doesn't require a client authentication certificate in the following scenarios:

- Clients use Microsoft Entra authentication.
- Clients use Configuration Manager token-based authentication.
- The Management Points enabled for CMG traffic are configured for Enhanced HTTP.

For more information, see Enable management point for HTTPS.

## Authentication Options

Management Points enabled for CMG traffic can be either EHTTP or HTTPS. If you can't join devices to Microsoft Entra ID or use PKI client authentication certificates, then use Configuration Manager token-based authentication. For more information, or to create a bulk registration token, see [Token-based authentication for cloud management gateway](../../deploy/deploy-clients-cmg-token).

### Enable management point for HTTPS

When you enable Enhanced HTTP, the site server generates a self-signed certificate named **SMS Role SSL Certificate**. This certificate is issued by the root **SMS Issuing** certificate. The management point adds this certificate to the IIS Default Web site bound to port 443.

With this option, internal clients can continue to communicate with the management point without any additional configuration. Internet-based clients using Microsoft Entra ID can securely communicate through the CMG with any management point enabled for EHTTP.

For more information, see [Enhanced HTTP](../../../plan-design/hierarchy/enhanced-http).

### Configure the management point for HTTPS

If Entra ID authentication is not available, configure a management point for HTTPS. First issue it a web server certificate, then enable the role for HTTPS.

1. Create and issue a web server certificate from your PKI or a third-party provider, which are outside of the context of Configuration Manager. For example, use Active Directory Certificate Services and group policy to issue a web server certificate to the site system server with the management point role. For more information, see the following articles:

    - [PKI certificate requirements](../../../plan-design/network/pki-certificate-requirements)
    - [Example deployment of PKI certificates: Deploy the web server certificate for site systems that run IIS](../../../plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012)
2. On the properties of the management point role, set the client connections to **HTTPS**.

    Tip

    After you set up the CMG, you'll configure other settings for this management point.

If your environment has multiple management points, you don't have to enable them all for CMG. Configure the CMG-enabled management points as **Internet only**. Then your on-premises clients don't try to use them.

#### Management point client connection mode summary

These tables summarize whether the management point requires EHTTP or HTTPS, depending upon the type of client. They use the following terms:

- *Workgroup*: The device isn't joined to a domain or Microsoft Entra ID, but has a client authentication certificate.
- *AD domain-joined*: You join the device to an on-premises Active Directory domain.
- *Microsoft Entra joined*: Also known as cloud domain-joined, you join the device to a Microsoft Entra tenant. For more information, see [Microsoft Entra joined devices](/en-us/azure/active-directory/devices/concept-azure-ad-join).
- *Hybrid-joined*: You join the device to your on-premises Active Directory and register it with your Microsoft Entra ID. For more information, see [Microsoft Entra hybrid joined devices](/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid).
- *HTTPS*: On the management point properties, you set the client connections to **HTTPS**.
- *E-HTTP*: On the site properties, **Communication Security** tab, you set the site system settings to **HTTPS or EHTTP**, and you enable the option to **Use Configuration Manager-generated certificates for HTTP site systems**. You configure the management point for EHTTP, and the management point is ready for CMG communication.

Important

Starting in Configuration Manager version 2103, sites that allow HTTP-only client communication are deprecated and the site must be configured for Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](../../../servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http).

##### For internet-based clients communicating with the CMG

Configure an on-premises management point to allow connections from the CMG with the following client connection mode:

| Internet-based client | Management point |
| --- | --- |
| Workgroup ^Note 1^ | E-HTTP, HTTPS |
| AD domain-joined ^Note 1^ | E-HTTP, HTTPS |
| Microsoft Entra joined | E-HTTP, HTTPS |
| Hybrid-joined | E-HTTP, HTTPS |

Note

**Note 1**: This configuration requires the client has a client authentication certificate, and only supports device-centric scenarios.

##### For on-premises clients communicating with the on-premises management point

Configure an on-premises management point with the following client connection mode:

| On-premises client | Management point |
| --- | --- |
| Workgroup | EHTTP, HTTPS |
| AD domain-joined | EHTTP, HTTPS |
| Microsoft Entra joined | EHTTP, HTTPS |
| Hybrid-joined | EHTTP, HTTPS |

Note

On-premises AD domain-joined clients support both device- and user-centric scenarios communicating with an EHTTP or HTTPS management point.