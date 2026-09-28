---
layout: Conceptual
title: Configure Microsoft Cloud PKI root and issuing CA for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/cloud-pki/configure-ca
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
ms.reviewer: wicale
ms.subservice: suite
description: Configure a root and issuing CA for the Microsoft Cloud PKI service.
ms.date: 2024-12-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c5d52850-f56e-3db7-95e3-41dd2ac20ac5
document_version_independent_id: c5d52850-f56e-3db7-95e3-41dd2ac20ac5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/cloud-pki/configure-ca.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: cloud-pki/configure-ca
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/cloud-pki/configure-ca.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: ef386f77-44c3-6896-3b97-39ce75f30e07
---

# Configure Microsoft Cloud PKI root and issuing CA for Microsoft Intune - Microsoft Intune | Microsoft Learn

This article describes how to create and deploy a Microsoft Cloud PKI root CA and issuing CA in Microsoft Intune. An issuing CA issues certificates to devices based on the certificate profiles you create in Intune.

## Prerequisites

For more information about how to prepare your tenant for Microsoft Cloud PKI, including key concepts and requirements, see:

- [Overview of Microsoft Cloud PKI for Intune](./): Review the architecture, tenant requirements, a feature summary, and known issues and limitations.
- [Deployment models](deployment-models): Review the Microsoft Cloud PKI deployment options.
- [Fundamentals](fundamentals): Review the PKI fundamentals and concepts that are important to know prior to configuration and deployment.

## Role based access control

The account you use to sign in to the Microsoft Intune admin center must have permission to create a certification authority (CA). The Microsoft Entra Intune Administrator (also known as Intune service administrator) role has the built-in permissions to create CAs. Alternatively, you can assign Cloud PKI CA permissions to an admin user. For more information, see [Role-based access control (RBAC) with Microsoft Intune](../fundamentals/role-based-access-control/overview).

## Step 1: Create root CA in admin center

Before you can start to issue certificates to managed devices, you need to create a root CA in your tenant to act as the trust anchor. This section describes how to create the root CA. At least one root CA must be created before an issuing CA can be created.

1. Sign in to the Microsoft Intune admin center.
2. Go to **Tenant administration** &gt; **Cloud PKI**, and then select **Create**.

    ![Microsoft Intune admin center Cloud PKI page with Create button highlighted.](media/shared/cloud-pki-create.png)
3. For **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the CA object. Name it so you can easily identify it later. Example: *Contoso C-PKI Root CA*
    - **Description**: Enter a description for the CA object. This setting is optional, but recommended. Example: *Microsoft Cloud PKI root CA for Contoso corporation*
4. Select **Next** to continue to **Configuration settings**.
5. Configure the following settings for the root CA:

    - **CA type**: Select **Root CA**.
    - **Validity period**: Select 5, 10, 15, 20, or 25 years. To create a root CA with a custom validity period, use the Microsoft Graph API. For more information, see [Intune Graph API overview](/en-us/graph/api/resources/intune-graph-overview).
6. For **Extended Key Usages**, select how you intend to use the CA.

    ![Configuration settings tab with Extended Key Usages section for Cloud PKI.](media/shared/cloud-pki-extended-key-usage.png)

    To prevent potential security risks, CAs are limited to select use. Your options:

    - **Type**: Select the purpose of the CA. The **Any Purpose (2.5.29.37.0)** EKU isn't for use, because it's overly permissive and a potential security risk. For more information about overly permissive certificate templates, see [Edit overly permissive certificates template with privileged EKU](/en-us/defender-for-identity/security-assessment-edit-overly-permissive-template#what-is-an-overly-permissive-certificate-template-with-privileged-eku).
    - Alternatively, to create a custom extended key usage, enter the **Name** and **Object Identifier**.

        Note

        Keep in mind that root CA EKU/OID constraints are a superset of the issuing CA. This means that when you create an issuing CA, you can only select the EKUs defined for the root CA. If you don't define the EKU in the root CA, it won't show up as an EKU option for the issuing CA.
7. Under **Subject attributes** enter a **Common name (CN)** for the root CA. Optionally, you can enter other attributes including:

    - Organization (O)
    - Country (C)
    - State or province (ST)
    - Locality (L)

    To adhere to PKI standards, Intune enforces a two-character limit for country/region.
8. Under **Encryption**, enter the **Key size and algorithm**. Your options:

    - **RSA-2048 and SHA-256**
    - **RSA-3096 and SHA-384**
    - **RSA-4096 and SHA-512**

    ![Key size and algorithm setting in Cloud PKI configuration settings.](media/configure-ca/key-size-algorithm.png)

    This setting enforces the upper bound key size and hash algorithm that can be used when configuring a device configuration SCEP certificate profile in Intune. It enables you to select any key size and hash up to what is set on the Cloud PKI issuing CA. Keep in mind a 1024 key size and SHA-1 hash isn't supported with Cloud PKI.
9. Select **Next** to continue to **Scope tags**.
10. Optionally, you can add scope tags to control visibility and access to this CA.
11. Select **Next** to continue to **Review + create**.
12. Review the summary provided. You won't be able to edit these properties after you create the CA. If needed, select **Back** to edit the settings and ensure they're correct and satisfy your PKI requirements. If later you need to add another EKU, you must create a new CA.
13. When you're ready to finalize everything, select **Create**.
14. Return to the Cloud PKI CA list in the admin center. Select **Refresh** to see your new CA.

    ![Microsoft Cloud PKI list with new root CA displayed.](media/configure-ca/cloud-pki-refresh.png)

## Step 2: Create issuing CA in admin center

An issuing CA is required to issue certificates for Intune-managed devices. Cloud PKI automatically provides a SCEP service that acts as a certificate registration authority. It requests certificates from the issuing CA on behalf of Intune-managed devices using a SCEP profile.

Note

With Microsoft Cloud PKI, you don't need to:

- Install and configure an NDES server.
- Install and configure the Intune certificate connector.
- Configure a proxy service to enable access to the NDES server URL.

1. Return to **Tenant administration** &gt; **Cloud PKI**.
2. Enter a **Name** and optional **Description** for so you can distinguish this CA from others in your tenant.
3. Select **Next** to continue to **Configuration settings**.
4. Select the CA type and root CA source.

    ![CA type and root CA source configuration with Intune option.](media/configure-ca/create-ca-configuration-settings.png)

    Your options:

    - **CA type**: Select **Issuing CA**. Then configure these additional settings:

        - **Root CA source**: Select **Intune**. This setting determines the root CA source anchoring the issuing CA.
        - **Root CA**: Select one of the root CAs you created in Intune to anchor against.
5. For **Validity period**, select 2, 4, 6, 8, or 10 years. The validity period of the issuing CA can't be longer than the root CA. To create an issuing CA with a custom validity period, use the Microsoft Graph API. For more information, see [Intune Graph API overview](/en-us/graph/use-the-api).
6. For **Extended Key Usages**, select how you intend to use the CA. To prevent potential security risks, CAs are limited to specific types of use. Your options:

    - **Type**: select the purpose of the CA. The **Any Purpose (2.5.29.37.0)** EKU isn't for use, because it's overly permissive and a potential security risk.
    - Alternatively, to create a custom EKU, enter the **Name** and **Object Identifier**.

        Note

        You can only select from EKUs defined in the root CA. If you didn't define an EKU in the root CA, it won't show up as an EKU option here.
7. Under **Subject attributes** enter a **Common name (CN)** for the issuing CA.

    ![Intune admin center Cloud PKI subject attributes settings.](media/configure-ca/subject-attributes-issuing.png)

    Optional attributes include:

    - Organization (O)
    - Organizational unit (OU)
    - Country (C)
    - State/province (ST)
    - Locality (L)

    To adhere to PKI standards, Intune enforces a two-character limit for country/region.
8. Select **Next** to continue to **Scope tags**.
9. Optionally, you can add scope tags to control visibility and access to this CA.
10. Select **Next** to continue to **Review + create**.
11. Review the summary provided. When you're ready to finalize everything, select **Create**.

    Tip

    You won't be able to edit these properties after you create the CA. If needed, select **Back** to edit the settings and ensure they are correct and satisfy your PKI requirements. If later you require additional EKUs, you must create a new CA.
12. Return to the Microsoft Cloud PKI CA list in the admin center. Select **Refresh** to see your new issuing CA.

    ![Microsoft Cloud PKI list with new issuing CA displayed.](media/configure-ca/cloud-pki-refresh-issuing.png)

To view the properties of root CAs and issuing CAs in your tenant, select the CA and then go to **Properties**. Available properties include:

- Certificate revocation list (CRL) distribution point URI
- Authority Information Access (AIA) URI
- SCEP URI - *issuing CA only*

Take note of these endpoint locations so you have them for later. Relying parties need network visibility to these endpoints. For example, you need to know the SCEP URI endpoint when you create SCEP profiles.

Note

The CRL is valid for 7 days, and is refreshed and republished in the admin center every 3.5 days. A refresh also happens every time an end-entity certificate is revoked.

When you create the trusted certificate profile required for Cloud PKI, you must have the public keys for the root CA certificates and issuing CA certificates. The public keys establish a chain of trust between Intune managed devices and Cloud PKI when requesting a certificate using SCEP certificate profiles. Select **Download** to download the public keys for these certificates. Repeat this step for every CA you have. The root and issuing CA certificates are also required to be installed on any relying parties, or authentication endpoints, supporting certificate-based authentication.

## Step 3: Create certificate profiles

To issue certificates, you must create a trusted certificate profile for your root and issuing CAs. The trusted certificate profile establishes trust with the Cloud PKI certificate registration authority supporting the SCEP protocol. A trusted certificate profile required for each platform (Windows, Android, iOS/iPad, macOS) that's issuing Cloud PKI SCEP certificates.

This step requires you to:

- Create a trusted certificate profile for the Cloud PKI root CA.
- Create a trusted certificate profile for a Cloud PKI issuing CA.
- Create an SCEP certificate profile for a Cloud PKI issuing CA.

### Create trusted certificate profile

In the admin center, create a trusted certificate profile for each OS platform you're targeting. Create one trusted certificate profile for the root CA certificate and one for the issuing CA. For instructions, see [Create a trusted certificate profile](../device-configuration/certificates/trusted-root-profiles#to-create-a-trusted-certificate-profile).

When prompted to, enter the public keys for the root CA and issuing CA. Complete the following steps to download the public keys for your CAs.

For the root CA:

1. Sign in to the Microsoft Intune admin center.
2. Go to **Tenant administration** &gt; **Cloud PKI**.
3. Select a CA that has a root type.
4. Go to **Properties**.
5. Select **Download**. Wait while the public key downloads.

For the issuing CA:

1. Return to your **Cloud PKI** list.
2. Select a CA that has an issuing type.
3. Go to **Properties**.
4. Select **Download**. Wait while the public key downloads.

The Cloud PKI root CA and issuing CA you download must be installed on all relying parties.

The file name given to the downloaded public keys is based on the Common Names specified in the CA. Some browsers, like Microsoft Edge, show a warning if you download a file with a .cer or other well-known certificate extension. If you receive this warning, select **Keep**.

![Downloads prompt with Keep option.](media/shared/download-warning.png)

### Create SCEP certificate profile

Note

Only Cloud PKI issuing CAs (including BYOCA issuing CA) can be used to issue SCEP certificates to Intune managed devices.

Just like you did for the trusted certificate profiles, create an SCEP certificate profile for each OS platform you're targeting. The SCEP certificate profile is used to request a leaf *client authentication* certificate from the issuing CA. This type of certificate is used in certificate based authentication scenarios, for things like Wi-Fi and VPN access.

1. Return to **Tenant administration** &gt; **Cloud PKI**.
2. Select a CA that has an **Issuing** type.
3. Go to **Properties**.
4. Next to the SCEP URI property, select **Copy to clipboard**.
5. In the admin center, create a SCEP certificate profile for each OS platform you're targeting. For instructions, see [Create a SCEP certificate profile](../device-configuration/certificates/scep-profiles#create-a-scep-certificate-profile).
6. In the profile, under **Root Certificate**, link the trusted certificate profile. The trusted certificate you select must be the root CA certificate that the issuing CA is anchored to in the CA hierarchy.

    ![Root certificate setting with root CA certificate selected.](media/shared/scep-root-certificate.png)
7. For **SCEP Server URLS**, paste the SCEP URI. It's important to leave the string `{{CloudPKIFQDN}}` as-is. Intune replaces this placeholder string with the appropriate FQDN when the profile is delivered to the device. The FQDN will appear within the \*.manage.microsoft.com namespace, a core Intune endpoint. For a complete list of Intune endpoints, see [Network Endpoints for Microsoft Intune](../fundamentals/endpoints).
8. Configure the remaining settings, following these best practices:

    - **Subject name format**: Ensure the variables specified are available on the user or device object in Microsoft Entra ID. For example, if the target user of this profile doesn't have an email address attribute but the email address in this profile is filled in, the certificate won't be issued. An error also appears in the SCEP certificate profile report.
    - **Extended Key Usage** (EKU): Microsoft Cloud PKI doesn't support the **Any Purpose** option.

        Note

        Make sure the EKU(s) you select is configured on the Cloud PKI issuing certificate authority (CA). If you select an EKU that isn't present on the Cloud PKI issuing CA, then an error occurs with the SCEP profile. And, a certificate isn't issued to the device.
    - **SCEP Server URLs**: Don't combine NDES and SCEP URLs with Microsoft Cloud PKI issuing CA SCEP URLs.
9. Assign and review the profile. When you're ready to finalize everything, select **Create**.