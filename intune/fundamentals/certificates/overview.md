---
layout: Conceptual
title: Types of certificate that are supported by Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- certificates
- sub-certificates
ms.reviewer: wicale
ms.subservice: fundamentals
description: Learn about Microsoft Intune's support for Simple Certificate Enrollment Protocol (SCEP), Public Key Cryptography Standards (PKCS) certificates.
ms.date: 2024-10-04T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: 2bddc5e4-5915-34a4-450c-9fd5d5df7fb9
document_version_independent_id: 2bddc5e4-5915-34a4-450c-9fd5d5df7fb9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/certificates/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/certificates/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/certificates/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d82f268f-3832-8760-1f05-0d9ad251d5dd
---

# Types of certificate that are supported by Microsoft Intune - Microsoft Intune | Microsoft Learn

Use certificates with Intune to authenticate your users to applications and corporate resources through VPN, Wi-Fi, or email profiles. When you use certificates to authenticate these connections, your end users don't need to enter usernames and passwords, which can make their access seamless. Certificates are also used for signing and encryption of email using S/MIME.

## Introduction to certificates with Intune

Certificates provide authenticated access without delay through the following two phases:

- Authentication phase: The user's authenticity is checked to confirm the user is who they claim to be.
- Authorization phase: The user is subjected to conditions for which a determination is made on whether the user should be given access.

Typical use scenarios for certificates include:

- Network authentication (for example, 802.1x) with device or user certs
- Authenticating with VPN servers using device or user certs
- Signing e-mail based on user certs

Intune supports Simple Certificate Enrollment Protocol (SCEP), Public Key Cryptography Standards (PKCS), and imported PKCS certificates as methods to provision certificates on devices. The different provisioning methods have different requirements, and results. For example:

- SCEP provisions certificates that are unique to each request for the certificate.
- PKCS provisions each device with a unique certificate.
- With Imported PKCS, you can deploy the same certificate that you've exported from a source, like an email server, to multiple recipients. This shared certificate is useful to ensure all your users or devices can then decrypt emails that were encrypted by that certificate.

To provision a user or device with a specific type of certificate, Intune uses a certificate profile.

In addition to the three certificate types and provisioning methods, you need a trusted root certificate from a trusted Certification Authority (CA). The CA can be an on-premises Microsoft Certification Authority, or a [third-party Certification Authority](third-party-ca-scep). The trusted root certificate establishes a trust from the device to your root or intermediate (issuing) CA from which the other certificates are issued. To deploy this certificate, you use the *trusted certificate* profile, and deploy it to the same devices and users that receive the certificate profiles for SCEP, PKCS, and imported PKCS.

Tip

Intune also supports use of [Derived credentials](../../device-security/certificates/derived-credentials) for environments that require use of smartcards.

### What's required to use certificates

- **A Certification Authority**. Your CA is the source of trust that the certificates reference for authentication. You can use a Microsoft CA or a third-party CA.
- **On-premises infrastructure**. The infrastructure you require depends on the certificate types you use:
    - [SCEP](scep-infrastructure)
    - [PKCS](../../device-configuration/certificates/pkcs-profiles)
    - [Imported PKCS](../../device-configuration/certificates/imported-pfx-profiles)
- **A trusted root certificate**. Before you deploy SCEP or PKCS certificate profiles, deploy the trusted root certificate from your CA using a *trusted certificate* profile. This profile helps establish the trust from the device back to the CA and is required by the other certificate profiles.

With a trusted root certificate deployed, you're ready to deploy certificate profiles to provision users and devices with certificates for authentication.

### Which certificate profile to use

The following comparisons aren't comprehensive but intended to help distinguish the use of the different certificate profile types.

| Profile type | Details |
| --- | --- |
| Trusted certificate | Use to deploy the public key (certificate) from a root CA or intermediary CA to users and devices to establish a trust back to the source CA. Other certificate profiles require the trusted certificate profile and its root certificate. |
| SCEP certificate | Deploys a template for a certificate request to users and devices. Each certificate that's provisioned using SCEP is unique and tied to the user or device that requests the certificate. With SCEP, you can deploy certificates to devices that lack a user affinity, including use of SCEP to provision a certificate on KIOSK or user-less device. |
| PKCS certificate | Deploys a template for a certificate request that specifies a certificate type of either user or device.  - Requests for a certificate type of user always require user affinity. When deployed to a user, each of the user's devices receives a unique certificate. When deployed to a device with a user, that user is associated with the certificate for that device. When deployed to a userless device, no certificate is provisioned.  - Templates with a certificate type of device don't require user affinity to provision a certificate. Deployment to a device provisions the device. Deployment to a user provisions the device the user is signed in to with a certificate. |
| PKCS imported certificate | Deploys a single certificate to multiple devices and users, which supports scenarios like S/MIME signing and encryption. For example, by deploying the same certificate to each device, each device can decrypt email received from that same email server. Other certificate deployment methods are insufficient for this scenario, as SCEP creates a unique certificate for each request, and PKCS associates a different certificate for each user, with different users receiving different certificates. |

## Intune supported certificates and usage

| Type | Authentication | S/MIME Signing | S/MIME encryption |
| --- | --- | --- | --- |
| Public Key Cryptography Standards (PKCS) imported certificate |  | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| PKCS#12 (or PFX) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |  |
| Simple Certificate Enrollment Protocol (SCEP) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |  |

To deploy these certificates, create and assign certificate profiles to devices.

Each individual certificate profile you create supports a single platform. For example, if you use PKCS certificates, you create PKCS certificate profile for Android and a separate PKCS certificate profile for iOS/iPadOS. If you also use SCEP certificates for those two platforms, you create a SCEP certificate profile for Android, and another for iOS/iPadOS.

### General considerations when you use a Microsoft Certification Authority

When you use a Microsoft Certification Authority (CA):

- To use SCEP certificate profiles:

    - [setup a Network Device Enrollment Service (NDES) server](scep-infrastructure#set-up-ndes) for use with Intune.
    - [Install the Certificate Connector for Microsoft Intune](connector/setup-connector).
- To use PKCS certificate profiles:

    - [Install the Certificate Connector for Microsoft Intune](connector/setup-connector).
- To use PKCS imported certificates:

    - [Install the Certificate Connector for Microsoft Intune](connector/setup-connector).
    - Export certificates from the certification authority and then import them to Microsoft Intune. See [the PFXImport PowerShell project](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).
- Deploy certificates by using the following mechanisms:

    - [Trusted certificate profiles](../../device-configuration/certificates/trusted-root-profiles) to deploy the Trusted Root CA certificate from your root or intermediate (issuing) CA to devices
    - SCEP certificate profiles
    - PKCS certificate profiles
    - PKCS imported certificate profiles

### General considerations when you use a third-party Certification Authority

When you use a third-party (non-Microsoft) Certification Authority (CA):

- SCEP certificate profiles don't require use of the Microsoft Intune Certificate Connector. Instead, the third-party CA handles the certificate issuance and management directly. To use SCEP certificate profiles without the Intune Certificate Connector:

    - Configure integration with a third-party CA from [one of our supported partners](third-party-ca-scep#third-party-certification-authority-partners). Setup includes following the instructions from the third-party CA to complete integration of their CA with Intune.
    - [Create an application in Microsoft Entra ID](third-party-ca-scep#set-up-third-party-ca-integration) that delegates rights to Intune to do SCEP certificate challenge validation.

    For more information, see [Set up third-party CA integration](third-party-ca-scep#set-up-third-party-ca-integration)
- PKCS imported certificates require use of the Microsoft Intune Certificate Connector. See [Install the Certificate Connector for Microsoft Intune](connector/setup-connector).
- Deploy certificates by using the following mechanisms:

    - [Trusted certificate profiles](../../device-configuration/certificates/trusted-root-profiles#create-trusted-certificate-profiles) to deploy the Trusted Root CA certificate from your root or intermediate (issuing) CA to devices
    - SCEP certificate profiles
    - PKCS certificate profiles *(only supported with the [Digicert PKI Platform](digicert-pkcs))*
    - PKCS imported certificate profiles

## Supported platforms and certificate profiles

| Platform | Trusted certificate profile | PKCS certificate profile | SCEP certificate profile | PKCS imported certificate profile |
| --- | --- | --- | --- | --- |
| Android device administrator | ![](media/overview/green-check.png)*(see **Note 1**)* | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| Android Enterprise  - Fully Managed (Device Owner) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| Android Enterprise  - Dedicated (Device Owner) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| Android Enterprise  - Corporate-Owned Work Profile | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| Android Enterprise  - Personally-Owned Work Profile | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| Android (AOSP) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |  |
| iOS/iPadOS | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| macOS | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) | ![](media/overview/green-check.png) |
| Windows 8.1 and later | ![](media/overview/green-check.png) |  | ![](media/overview/green-check.png) |  |
| Windows | ![](media/overview/green-check.png)*(see **Note 2**)* | ![](media/overview/green-check.png)*(see **Note 2**)* | ![](media/overview/green-check.png)*(see **Note 2**)* | ![](media/overview/green-check.png) |

- ***Note 1*** - Beginning with Android 11, trusted certificate profiles can no longer install the trusted root certificate on devices that are enrolled as *Android device administrator*. This limitation doesn't apply to Samsung Knox. For more information, see [Trusted certificate profiles for Android device administrator](../../device-configuration/certificates/trusted-root-profiles#trusted-certificate-profiles-for-android-device-administrator).
- ***Note 2*** - This profile is supported for [Windows Enterprise multi-session remote desktops](../../solutions/azure-virtual-desktop-multi-session).

Important

On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).