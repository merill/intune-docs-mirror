---
layout: Conceptual
title: Renew a Certificate Authority in Cloud PKI - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/cloud-pki/renew-ca
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
description: Learn how to renew a certificate authority (CA) in Microsoft Cloud PKI to maintain continuous certificate issuance.
ms.date: 2026-01-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 0520582e-56cf-ac69-82cb-433050139ef5
document_version_independent_id: 0520582e-56cf-ac69-82cb-433050139ef5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/cloud-pki/renew-ca.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: cloud-pki/renew-ca
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/cloud-pki/renew-ca.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 2d4278ae-44d3-89ed-4080-557dffa61d80
---

# Renew a Certificate Authority in Cloud PKI - Microsoft Intune | Microsoft Learn

Microsoft Cloud PKI supports renewing certificate authorities (CAs) to help you maintain continuous certificate issuance and avoid service disruptions as certificates approach expiration.

CA renewal creates a new CA certificate with updated cryptographic material while preserving access to certificates and certificate revocation lists (CRLs) issued by earlier CA versions.

This article provides an overview of how CA renewal works, when renewal is available, and what to expect during the renewal lifecycle.

## Prerequisites

To renew a certificate authority in Cloud PKI, ensure you meet the following prerequisites:

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To renew a certificate authority, use an account with at least the following [Cloud PKI permissions](../fundamentals/role-based-access-control/create-custom-role#cloud-pki):
> 
> - **Read CAs**
> - **Create certificate authorities (CAs)**
> 

![cloud-pki-icon](icons/cloud-pki.svg)**CA requirements**

> 
> The certificate renewal applies to the following CA types:
> 
> - Intune-managed issuing CAs
> - Bring your own CA (BYOCA) issuing CAs
> 

## How it works

Renewing a certificate authority issues a new CA certificate with a new public/private key pair. The renewed CA extends the lifetime of the certificate authority beyond the expiration date of the original certificate. Key characteristics of CA renewal include:

- A new key pair is always generated during renewal.
- Existing public/private key pairs can't be reused.
- Certificates and CRLs issued by earlier CA versions remain available after renewal.
- Renewal can be performed using the Intune admin center or Microsoft Graph.

Cloud PKI uses a staged renewal model that lets you validate a renewed CA before making it active. The renewal process involves three main steps:

**1. Renew the CA**

![](icons/renew.svg)

> 
> A CA becomes eligible for renewal when it reaches half of its validity lifetime or has expired. Once eligible, the CA can be renewed to create a staged version.
> 
> As a CA approaches expiration, Intune displays banners and status indicators to help administrators identify when action is required. The renewal process differs slightly depending on whether you're using an Intune-managed CA or a bring your own CA (BYOCA) deployment.
> 
> Expired CAs can still be renewed; however, certificate issuance is unavailable until the staged CA is activated.

**2. Test the staged CA**

![](icons/stage.svg)

> 
> Selecting **Renew** creates a staged version of the issuing CA.
> 
> The staged CA:
> 
> - Has a temporary **SCEP URI** for testing, separate from the production SCEP URI.
> - Can be used to validate certificate issuance before activation.
> - Is available for up to 90 days.
> 
> 
> If a staged CA isn't activated:
> 
> - It becomes inactive after 90 days.
> - It's deleted after an additional 30‑day grace period.
> - Hardware security module (HSM) resources are reclaimed.
> 

**3. Activate the CA**

![](icons/activate.svg)

> 
> Promote the staged CA to active to complete the renewal.
> 
> Activating the staged CA:
> 
> - Promotes the staged CA to Active.
> - Retires the previously active CA.
> - Disables the staged SCEP URI.
> - Restores use of the original production SCEP URI, so existing SCEP profiles don't need to be updated.
> 

## Renewal naming and versioning

Each CA renewal increments the CA version and updates the CA display name to reflect that version.

When an issuing CA is renewed, Intune appends a version suffix to the CA display name using the format: `(V#.0)`. Each renewal increments the version number by 1.

Examples:

- Before renewal: `Contoso-PKI-Issuing-CA`
- After first renewal: `Contoso-PKI-Issuing-CA (V2.0)`
- After second renewal: `Contoso-PKI-Issuing-CA (V3.0)`

The version suffix is applied at renewal time and becomes the CA object name used in Intune.

## Check a certificate authority details

To verify the details of a certificate authority in Cloud PKI:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus) &gt; [**Cloud PKI**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/caManagement).
    - In the list of certificate authorities, the **Renewal** field indicates whether action is required or the current status of the CA renewal.
2. Select a certificate authority.
    - The **Monitor** tab provides an overview of an issuing CA activity, including the number of active, expired, and revoked certificates.
    - The **Properties**tab displays the current status, Active version, and settings of the CA. Details in this tab include:
        - Name
        - Description
        - Status
        - CA version
        - Serial number
        - Thumbprint
        - CA type
        - CA keys
        - Extended Key Usages
        - Valididty period
        - Expiration
        - Common name (CN)
        - Organization (O)
        - Organizational unit (OU)
        - Country (C)
        - State or province (ST)
        - Locality (L)
        - Key size and algorithm
        - CRL distribution point
        - SCEP URI
        - Download certificate (public key)
    - The **Versions**tab to track and manage staged, and prior CA versions. Details in this tab include:
        - A list of current and prior CA versions
        - A dedicated pane with details about each CA version, including the options to **Activate** or **Revoke** a staged CA.

## Renew a certificate authority

To renew a certificate authority in Cloud PKI, the steps are different depending on whether you're using an Intune-managed CA or a *bring your own CA* deployment. Select the tab for your scenario:

# [Intune-managed CA](#tab/ica)
1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus) &gt; [**Cloud PKI**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/caManagement).
2. Select the certificate authority you want to renew.
3. If the CA is eligible for renewal, the **Renew** option is available on the command bar. Select **Renew**. The **Renew** option is disabled when the CA renewal status is *staged*.
4. Review the information in the **Renew Certification Authority** pane, and then select **Renew**.
5. A staged CA and staged SCEP URI are created.

Note

After the staged CA is created, the renewal status of the issuing CA changes to **Staged**.

# [Bring your own CA](#tab/byoca)
1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus) &gt; [**Cloud PKI**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/caManagement).
2. Select the certificate authority you want to renew.
3. If the CA is eligible for renewal, the **Renew** option is available on the command bar. Select **Renew**. The **Renew** option is disabled when the CA renewal status is *signing required* or *staged*.
4. Review the information in the **Renew Certification Authority** pane, and then select **Renew**.
5. A certificate signing request (CSR) is generated. Select **Download CSR**.
6. Sign the CSR using your on-premises or private CA that issued the original certificate. For more information, see [Sign certificate signing request](configure-byoca#step-2-sign-certificate-signing-request).
7. Select **Upload signed certificate**.
8. The **Upload signed certificate** window opens. Under **Upload signed certificate (.cer, .crt, or .pem) file**, select **Browse**. Choose the signed certificate file.
9. After upload and successful validation, a staged CA and staged SCEP URI are created. or

Note

- During the renewal process, the renewal status of the issuing CA changes to **Signing required** until the signed certificate is uploaded and validated.
- After the staged CA is created, the renewal status of the issuing CA changes to **Staged**.

---

Use the staged certificate authority (CA) and its temporary SCEP URI to validate certificate issuance before activation. Create and assign a SCEP profile using the staged SCEP URI to test groups. After validation is complete, remove the test SCEP profile.

The staged CA is available for up to 90 days. If it isn't activated within that period, it becomes inactive and is deleted after an additional 30-day grace period.

Tip

The staged CA allows up to 50 test certificates to be issued during the 90-day staged period. This helps you validate certificate issuance without impacting production environments.

## Activate a staged certificate authority

The last step in the renewal process is to activate the staged certificate authority.

To activate a certificate authority in Cloud PKI:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus) &gt; [**Cloud PKI**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/caManagement).
2. Select the staged certificate authority you want to activate.
3. Select the **Versions** tab.
4. In the list of CA versions, select the CA that has the **Staged** status.
5. In the details pane, select **Activate**.

After activation, the staged SCEP URI is removed and the previous CA version is retired.

## Revoke a staged certificate authority

In case you need to cancel a staged certificate authority before activation, you can revoke it.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/tenantStatus) &gt; [**Cloud PKI**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/caManagement).
2. Select the staged certificate authority you want to activate.
3. Select the **Versions** tab.
4. In the list of CA versions, select the CA that has the **Staged** status.
5. In the details pane, select **Revoke**.

## Certificate authority renewal notifications and status

The Intune admin center provides renewal notifications and status to help you track CAs as they approach expiration.

### Certificate renewal banners

A certification authority is eligible for renewal when it is halfway to expiration (half-life). The following table shows the renewal banners displayed in the Intune admin console Cloud PKI list based on the number of days prior to expiration.

| Icon | Renewal banner | Description |
| --- | --- | --- |
| ![info-icon](../media/icons/16/info-gray.svg) | **Halfway to expiration** | Certification authority is halfway to expiration. This marks the midpoint of the certificate authority's lifecycle. Review your renewal plan based on your organization's PKI policy. |
| ![error-icon](../media/icons/16/error.svg) | **6 months remaining** | Certification authority expires in 6 months. Renew now to ensure certificate issuance continues for SCEP, Wi-Fi, VPN, and email. |
| ![error-icon](../media/icons/16/error.svg) | **90 days** | Certification authority expires in 90 days. Renew now to ensure certificate issuance continues for SCEP, Wi-Fi, VPN, and email. |
| ![error-icon](../media/icons/16/error.svg) | **30 days** | Certification authority expires in 30 days. Without renewal, new certificate issuance could fail. Existing certificates stay valid until they expire. Renew now to maintain device certificate delivery. |
| ![error-icon](../media/icons/16/error.svg) | **Expired** | Certification authority has expired. Certificates are no longer issued. Renew or create a new certification authority to restore certificate issuance. |

### Certificate authority status values

Cloud PKI CA list has a **Status** field that indicates the current certification authority lifecycle state.

| Status | Description |
| --- | --- |
| **Active** | A CA that is currently issuing certificates. |
| **Expired** | A CA that has reached the end of its validity period. |
| **Revoked** | A CA that was explicitly revoked by an admin. |
| **Paused** | A CA that still has validity but has been paused by an admin. |
| **Signing required** | Applies only to BYOCA renewals that require a signed CSR. |

Cloud PKI CA list has a **Renewal** field that indicates the certification authority renewal state.

| Renewal | Description |
| --- | --- |
| **Action required** | A CA that is eligible for renewal. |
| **Staged** | A renewed CA available for testing before activation. |
| **Signing required** | Applies only to BYOCA renewals that require a signed CSR. |

When you open a certificate authority from the list, the **Versions** tab provides a list of the current and prior CAs. The **Status** field indicates the lifecycle state of each.

| Status | Description |
| --- | --- |
| **Active** | A CA that is currently issuing certificates. |
| **Staged** | A renewed CA available for testing before activation. |
| **Retired** | A previous CA that has been replaced by an active renewal. |
| **Expired** | A CA that has reached the end of its validity period. |
| **Revoked** | A CA that was explicitly revoked by an admin. |
| **Decommissioned** | A staged CA that wasn't activated and exceeded its lifetime. |
| **Paused** | A CA that still has validity but has been paused by an admin. |
| **Signing required** | Applies only to BYOCA renewals that require a signed CSR. |