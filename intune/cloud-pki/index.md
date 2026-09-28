---
layout: Conceptual
title: Microsoft Cloud PKI for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/cloud-pki/
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
description: An overview of the Microsoft Cloud PKI service, available with Microsoft Intune Suite or as a standalone capability.
ms.date: 2026-09-08T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: 96dd180f-c64f-d341-9317-549a231ab7d5
document_version_independent_id: 96dd180f-c64f-d341-9317-549a231ab7d5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/cloud-pki/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: cloud-pki/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/cloud-pki/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 287bcd92-2e68-f9a6-c0a4-8cd391da3055
---

# Microsoft Cloud PKI for Microsoft Intune - Microsoft Intune | Microsoft Learn

Use Microsoft Cloud PKI to issue certificates for Intune-managed devices. Microsoft Cloud PKI is a cloud-based service that simplifies and automates certificate lifecycle management for Intune-managed devices. It provides a dedicated public key infrastructure (PKI) for your organization, without requiring any on-premises servers, connectors, or hardware. It handles the certificate issuance, renewal, and revocation for all Intune supported platforms.

This article provides an overview of Microsoft Cloud PKI for Intune, how it works, and its architecture.

## What is PKI?

PKI is a system that uses digital certificates to authenticate and encrypt data between devices and services. PKI certificates are essential for securing various scenarios, such as VPN, Wi-Fi, email, web, and device identity. However, managing PKI certificates can be challenging, costly, and complex, especially for organizations that have a large number of devices and users. You can use Microsoft Cloud PKI to enhance the security and productivity of your devices and users, and to accelerate your digital transformation to a fully managed cloud PKI service. Additionally, you can utilize the Cloud PKI service in to reduce workloads for Active Directory Certificate Services (ADCS) or private on-premises certification authorities.

## Prerequisites

![](../media/icons/16/licensing.svg)**Licensing requirements**

> 
> This feature requires a subscription in addition to Microsoft Intune Plan 1 or Plan 2. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

Note

Microsoft Cloud PKI is available in GCC High environments. It isn't available in DoD environments.

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> You can use the Microsoft Cloud PKI service with these platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - Windows
> 
> 
> Devices must be enrolled in Intune, and the platform must support the Intune device configuration SCEP certificate profile.

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> The following permissions are available to assign to custom Intune roles. These permissions enable users to view and manage CAs in the admin center.
> 
> - Read CAs: Any user assigned this permission can read the properties of a CA.
> - Create certificate authorities: Any user assigned this permission can create a root or issuing CA.
> - Revoke issued leaf certificates: Any user assigned this permission has the ability to manually revoke a certificate issued by an issuing CA. This permission also requires the *read CA* permission.
> 
> 
> You can assign scope tags to the root and issuing CAs. For more information about how to create custom roles and scope tags, see [Role-based access control with Microsoft Intune](../fundamentals/role-based-access-control/scope-tags).

## Manage Cloud PKI in Microsoft Intune admin center

Microsoft Cloud PKI objects are created and managed in the Microsoft Intune admin center. From there, you can:

- Set up and use Microsoft Cloud PKI for your organization.
- Enable Cloud PKI in your tenant.
- Create and assign certificate profiles to devices.
- Monitor issued certificates.

After you create a Cloud PKI issuing CA, you can start to issue certificates in minutes.

## Overview of features

The following table lists the features and scenarios supported with Microsoft Cloud PKI and Microsoft Intune.

| Feature | Overview |
| --- | --- |
| Create multiple certificate authorities (CA) in an Intune tenant | Create two-tier PKI hierarchy with root and issuing CA in the cloud. |
| Bring your own CA (BYOCA) | Anchor an Intune Issuing CA to a private CA through Active Directory Certificate Services or a non-Microsoft certificate service. If you have an existing PKI infrastructure, you can maintain the same root CA and create an issuing CA that chains to your external root. This option includes support for external private CA N+ tier hierarchies. |
| Signing and Encryption algorithms | Intune supports RSA, key sizes 2048, 3072, and 4096. |
| Hash algorithms | Intune supports SHA-256, SHA-384, and SHA-512. |
| HSM keys (signing and encryption) | Keys are provisioned using [Azure Managed Hardware Security Module (Azure Managed HSM)](/en-us/azure/key-vault/managed-hsm/overview).  Cloud PKI CAs use HSM signing and encryption keys. No Azure subscription is required for Azure HSM. |
| Software Keys (signing and encryption) | CAs created during a trial period of Intune Suite or standalone Cloud PKI use software-backed signing and encryption keys using `System.Security.Cryptography.RSA`. |
| Certificate registration authority | Providing a Cloud Certificate Registration Authority supporting Simple Certificate Enrollment Protocol (SCEP) for each Cloud PKI Issuing CA. |
| Certificate Revocation List (CRL) distribution points | Intune hosts the CRL distribution point (CDP) for each CA.  The CRL validity period is seven days. Publishing and refresh happen every 3.5 days. The CRL is updated with every certificate revocation. |
| Authority Information Access (AIA) end points | Intune hosts the AIA endpoint for each Issuing CA. The AIA endpoint can be used by relying parties to retrieve parent certificates. |
| End-entity certificate issuance for users and devices | Also referred to as *leaf certificate* issuance. Support is for the SCEP (PKCS#7) protocol and certification format, and Intune-MDM enrolled devices supporting the SCEP profile. |
| Certificate life-cycle management | Issue, renew, and revoke end-entity certificates. |
| Reporting dashboard | Monitor active, expired, and revoked certificates from a dedicated dashboard in the Intune admin center. View reports for issued leaf certificates and other certificates, and revoke leaf certificates. Reports are updated every 24 hours. |
| Auditing | Audit admin activity such as create, revoke, and search actions in the Intune admin center. |
| Role-based access control (RBAC) permissions | Create custom roles with Microsoft Cloud PKI permissions. The available permissions enable you to read CAs, disable and reenable CAs, revoke issued leaf certificates, and create certificate authorities. |
| Scope tags | Add scope tags to any CA you create in the admin center. Scope tags can be added, deleted, and edited. |

## Architecture

Microsoft Cloud PKI is made up of several key components working together to simplify the complexity and management of a public key infrastructure. It includes a Cloud PKI service for creating and hosting certification authorities, combined with a certificate registration authority to automatically service incoming certificate requests from Intune-enrolled devices. The registration authority supports the Simple Certificate Enrollment Protocol (SCEP).

![Microsoft Cloud PKI architecture showing Cloud PKI service, certification authorities, certificate registration authority, and SCEP communication with Intune-enrolled devices.](media/index/architecture-flow.png)

`*` See **Components** for a breakdown of services.

**Components**:

- A - Microsoft Intune
- B - Microsoft Cloud PKI services

    - B1 - Microsoft Cloud PKI service
    - B2 - Microsoft Cloud PKI SCEP service
    - B3 - Microsoft Cloud PKI SCEP validation service

    The *certificate registration authority* makes up B2 and B3 in the diagram.

These components replace the need for an on-premises certificate authority, NDES, and Intune certificate connector.

**Actions**:

Before the device checks in to the Intune service, an Intune administrator or Intune role with permissions to manage the Microsoft Cloud PKI service must complete the following actions:

- Create the required Cloud PKI certification authority for the root and issuing CAs in Microsoft Intune.
- Create and assign the required trust certificate profiles for the root and issuing CAs.
- Create and assign the required platform-specific SCEP certificate profiles.

These actions require components B1, B2, and B3.

Note

A Cloud PKI Issuing Certification Authority is required to issue certificates for Intune managed devices. Cloud PKI provides a SCEP service that acts as a Certificate Registration Authority. The service requests certificates from the Issuing CA on behalf of Intune-managed devices using a SCEP profile.

The flow continues with the following actions, shown in the diagram as A1 through A5:

A1. A device checks in with the Intune service and receives the trusted certificate and SCEP profiles.

A2. Based on the SCEP profile, the device creates a certificate signing request (CSR). The private key is created on the device, and never leaves the device. The CSR and the SCEP challenge are sent to the SCEP service in the cloud (SCEP URI property in the SCEP profile). The SCEP challenge is encrypted and signed using the Intune SCEP RA keys.

A3. The SCEP validation service verifies the CSR against the SCEP challenge. Validation ensures the request comes from an enrolled and managed device. It also ensures the challenge is untampered, and that it matches the expected values from the SCEP profile. If any of these checks fail, the certificate request is rejected.

A4. After the CSR is validated, the SCEP validation service, also known as the *registration authority*, requests that the issuing CA signs the CSR.

A5. The signed certificate is delivered to the Intune MDM-enrolled device.

Note

The SCEP challenge is encrypted and signed using the Intune SCEP registration authority keys.

## Try Microsoft Cloud PKI

You can try out the Microsoft Cloud PKI feature in the Intune admin center during a trial period. Available trials include:

- [Microsoft Intune Suite trial](https://aka.ms/MicrosoftIntunePricing)
- [Standalone Cloud PKI trial](../fundamentals/advanced-capabilities)

During the trial period, you can create up to three CAs in your tenant. Cloud PKI CAs created during the trial use software-backed keys, and use `System.Security.Cryptography.RSA` to generate and sign the keys. You can continue to use the CAs after purchasing a Cloud PKI license. However, the keys remain software-backed, and can't be converted to HSM backed keys. The Microsoft Intune service managed CA keys. No Azure subscription is required for Azure HSM capabilities.

## CA configuration examples

Two-tier Cloud PKI root & issuing CAs and bring-your-own CAs can coexist in Intune. You can use the following configurations, provided as examples, to create CAs in Microsoft Cloud PKI:

- One root CA with two issuing CAs
- One root CA with one issuing CA, and one bring-your-own CA.
- Three bring-your-own CAs

## Known issues and limitations

For the latest changes and additions, see [What's new in Microsoft Intune](../whats-new/).

- You can create up to three CAs in an Intune tenant.

    - Licensed Cloud PKI - A total of 3 CAs can be created using Azure mHSM keys.
    - Trial Cloud PKI - A total of 3 CAs can be created during a trial of Intune Suite or standalone Cloud PKI.
- The following CA types count toward the CA capacity:

    - Cloud PKI Root CA
    - Cloud PKI Issuing CA
    - BYOCA Issuing CA
- A [data residency option](../privacy/data-handling/data-storage-processing#data-residency-option) is currently not available to customers using Cloud PKI.