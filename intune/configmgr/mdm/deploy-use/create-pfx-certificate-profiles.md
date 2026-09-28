---
layout: Conceptual
title: Create PFX certificate profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/create-pfx-certificate-profiles
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
description: Learn how to use PFX files in Configuration Manager to generate user-specific certificates that support encrypted data exchange.
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b1d6a983-4fd7-e590-4ee4-eab195c10073
document_version_independent_id: cab2da4d-f936-2318-a511-1d68caa16f47
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/create-pfx-certificate-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/create-pfx-certificate-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/create-pfx-certificate-profiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: afa1ca6a-d335-8d00-1146-a6542da28b31
---

# Create PFX certificate profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Learn how to create a certificate profile that uses a certification authority for credentials. This article highlights specific information about personal information exchange (PFX) certificate profiles. For more information about how to create and configure these profiles, see [Certificate profiles](../../protect/deploy-use/introduction-to-certificate-profiles).

Configuration Manager allows you to create a PFX certificate profile using credentials issued by a certificate authority. You can choose Microsoft or Entrust as your certificate authority. When deployed to user devices, PFX files generate user-specific certificates to support encrypted data exchange.

To import certificate credentials from existing certificate files, see [Import PFX certificate profiles](import-pfx-certificate-profiles).

## Prerequisites

Before you start creating a certificate profile, make sure the necessary prerequisites are ready. For more information, see [Prerequisites for certificate profiles](../../protect/plan-design/prerequisites-for-certificate-profiles). For example, for PFX certificate profiles, you need a [certificate registration point](../../protect/deploy-use/certificate-infrastructure#step-2---install-and-configure-the-certificate-registration-point) site system role.

## Create a profile

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, expand **Company Resource Access**, and then select **Certificate Profiles**.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Create Certificate Profile**.
3. On the **General** page of the **Create Certificate Profile Wizard**, specify the following information:

    - **Name**: Enter a unique name for the certificate profile. You can use a maximum of 256 characters.
    - **Description**: Provide a description that gives an overview of the certificate profile that helps to identify it in the Configuration Manager console. You can use a maximum of 256 characters.
4. Select **Personal Information Exchange - PKCS #12 (PFX) settings - Create**. This option requests a certificate on behalf of a user from a connected on-premises certificate authority (CA). Choose your certificate authority: **Microsoft** or **Entrust**.

    Note

    The **Import** option gets information from an existing certificate to create a certificate profile. For more information, see [Import PFX certificate profiles](import-pfx-certificate-profiles).
5. On the **Supported Platforms** page, select the OS versions that this certificate profile supports. For more information on supported OS versions for your version of Configuration Manager, see [Supported OS versions for clients and devices](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
6. On the **Certificate Authorities** page, choose the certificate registration point (CRP) to process the PFX certificates:

    1. **Primary Site**: Choose the server containing the CRP role for the CA.
    2. **Certification authorities**: Select the relevant CA.

    For more information, see [Certificate infrastructure](../../protect/deploy-use/certificate-infrastructure).

The settings on the **PFX Certificate** page vary depending on the selected CA on the **General** page:

- Microsoft CA
- Entrust CA

### Configure **PFX Certificate** settings for Microsoft CA

1. For the **Certificate template name**, choose the certificate template.
2. To use the certificate profile for S/MIME signing or encryption, enable **Certificate usage**.

    When you enable this option, it delivers all PFX certificates associated with the target user to all of their devices. If you don't enable this option, each device receives a unique certificate.
3. Set **Subject name format** to either **Common name** or **Fully-distinguished name**. If you're unsure which one to use, contact your CA administrator.
4. For the **Subject alternative name**, enable **Email address** and **User principle name (UPN)** as appropriate for your CA.
5. **Renewal threshold**: Determines when certificates are automatically renewed, based on the percentage of time remaining before expiration.
6. Set the **Certificate validity period** to the lifetime of the certificate.
7. When the certificate registration point specifies Active Directory credentials, enable **Active Directory publishing**.
8. If you selected one or more Windows 10 supported platforms:

    1. Set the **Windows certificate store** to **User**. (The **Local Computer** option doesn't deploy certificates, don't choose it.)
    2. Select one of the following **Key Storage Provider (KSP)**:

        - **Install to Trusted Platform Module (TPM) if present**
        - **Install to Trusted Platform Module (TPM) otherwise fail**
        - **Install to Windows Hello for Business otherwise fail**
        - **Install to Software Key Storage Provider**
9. Complete the wizard.

### Configure **PFX Certificate** settings for Entrust CA

1. For the **Digital ID Configuration**, choose the configuration profile. The Entrust administrator creates the digital ID configuration options.
2. To use the certificate profile for S/MIME signing or encryption, enable **Certificate usage**.

    When you enable this option, it delivers all PFX certificates associated with the target user to all of their devices. If you don't enable this option, each device receives a unique certificate.
3. To map Entrust **Subject name format** tokens to Configuration Manager fields, select **Format**.

    The **Certificate Name Formatting** dialog lists the Entrust Digital ID configuration variables. For each Entrust variable, choose the appropriate Configuration Manager fields.
4. To map Entrust **Subject Alternative Name** tokens to supported LDAP variables, select **Format**.

    The **Certificate Name Formatting** dialog lists the Entrust Digital ID configuration variables. For each Entrust variable, choose the appropriate LDAP variable.
5. **Renewal threshold**: Determines when certificates are automatically renewed, based on the percentage of time remaining before expiration.
6. Set the **Certificate validity period** to the lifetime of the certificate.
7. When the certificate registration point specifies Active Directory credentials, enable **Active Directory publishing**.
8. If you selected one or more Windows 10 supported platforms:

    1. Set the **Windows certificate store** to **User**. (The **Local Computer** option doesn't deploy certificates, don't choose it.)
    2. Select one of the following **Key Storage Provider (KSP)**:

        - **Install to Trusted Platform Module (TPM) if present**
        - **Install to Trusted Platform Module (TPM) otherwise fail**
        - **Install to Windows Hello for Business otherwise fail**
        - **Install to Software Key Storage Provider**
9. Complete the wizard.

## Deploy the profile

After you create a certificate profile, it's now available in the **Certificate Profiles** node. For more information on how to deploy it, see [Deploy resource access profiles](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles).