---
layout: Conceptual
title: Sign and encrypt email using S/MIME - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/certificates/s-mime
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.reviewer: wicale
ms.subservice: protect
description: Learn how to use email digital certificates in Microsoft Intune to sign and encrypt emails on devices. These certificates are called S/MIME and are configured using device configuration profiles. Signing and encryption certificates use PKCS, or private certificates, and use a connector to import certificates.
ms.date: 2021-07-29T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-identity-device-management
- certificates
- sub-certificates
locale: en-us
document_id: bc93fd32-b5b4-3f70-1dff-6ad36877fa7a
document_version_independent_id: bc93fd32-b5b4-3f70-1dff-6ad36877fa7a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/certificates/s-mime.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/certificates/s-mime
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/certificates/s-mime.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9671d4c8-5789-7ada-b22a-815693591edc
---

# Sign and encrypt email using S/MIME - Microsoft Intune | Microsoft Learn

Email certificates, also known as S/MIME certificate, provide extra security to your email communications by using encryption and decryption. Microsoft Intune can use S/MIME certificates to sign and encrypt emails to mobile devices running the following platforms:

- Android
- iOS/iPadOS
- macOS
- Windows

Intune can automatically deliver S/MIME encryption certificates to all platforms. S/MIME certificates are automatically associated with mail profiles that use the native mail client on iOS, and with Outlook on iOS and Android devices. For the Windows and macOS platforms, and for other mail clients on iOS and Android, Intune delivers the certificates but users must manually enable S/MIME in their mail app and choose their S/MIME certificates.

For more information about S/MIME email signing and encryption with Exchange, see [S/MIME for message signing and encryption](/en-us/Exchange/policy-and-compliance/smime).

This article provides an overview of using S/MIME certificates to sign and encrypt emails on your devices.

## Signing certificates

Certificates used for signing allow the client email app to communicate securely with the email server.

To use signing certificates, create a template on your certificate authority (CA) that focuses on signing. On Microsoft Active Directory Certification Authority, [Configure the server certificate template](/en-us/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) lists the steps to create certificate templates.

Signing certificates in Intune use PKCS certificates. [Configure and use PKCS certificates](../../device-configuration/certificates/pkcs-profiles) describes how to deploy and use PKCS certificate in your Intune environment. These steps include:

- Install and configure the [Certificate Connector for Microsoft Intune](../../fundamentals/certificates/connector/setup-connector) to support PKCS certificate requests. The connector has the same network requirements as [managed devices](../../fundamentals/endpoints#access-for-managed-devices).
- Create a trusted root certificate profile for your devices. This step includes using trusted root and intermediate certificates for your certification authority, and then deploying the profile to devices.
- Create a PKCS certificate profile using the certificate template you created. This profile issues signing certificates to devices, and deploys the PKCS certificate profile to devices.

You can also import a signing certificate for a specific user. The signing certificate is deployed across any device that a user enrolls. To import certificates into Intune, use the [PowerShell cmdlets in GitHub](https://github.com/Microsoft/Intune-Resource-Access). To deploy a PKCS certificate imported in Intune to be used for email signing, follow the steps in [Configure and use PKCS certificates with Intune](../../device-configuration/certificates/pkcs-profiles). These steps include:

- Download, install, and configure the [Certificate Connector for Microsoft Intune](../../fundamentals/certificates/connector/setup-connector). This connector delivers imported PKCS certificates to devices.
- Import S/MIME email signing certificates to Intune.
- Create a PKCS imported certificate profile. This profile delivers imported PKCS certificates to the appropriate user's devices.

## Encryption certificates

Certificates used for encryption confirm that an encrypted email can only be decrypted by the intended recipient. S/MIME encryption is an extra layer of security that can be used in email communications.

When sending an encrypted email to another user, the public key of that user's encryption certificate is obtained, and encrypts the email you send. The recipient decrypts the email using the private key on their device. Users can have a history of certificates used to encrypt email. Each of those certificates must be deployed to all of a specific user's devices so their email is successfully decrypted.

It's recommended that email encryption certificates aren't created in Intune. While Intune supports issuing PKCS certificates that support encryption, Intune creates a unique certificate per device. A unique certificate per device isn't ideal for an S/MIME encryption scenario where the encryption certificate should be shared across all the user's devices.

To deploy S/MIME certificates using Intune, you must import all of a user's encryption certificates to Intune. Intune then deploys all of those certificates to each device that a user enrolls. To import certificates into Intune, use the [PowerShell cmdlets in GitHub](https://github.com/Microsoft/Intune-Resource-Access).

To deploy a PKCS certificate imported in Intune used for email encryption, follow the steps in [Configure and use PKCS certificates with Intune](../../device-configuration/certificates/pkcs-profiles). These steps include:

- Install and configure the [Certificate Connector for Microsoft Intune](../../fundamentals/certificates/connector/setup-connector). This connector delivers imported PKCS certificates to devices.
- Import S/MIME email encryption certificates to Intune.
- Create a PKCS imported certificate profile. This profile delivers imported PKCS certificates to the appropriate user's devices.

Note

Imported S/MIME encryption certificates are removed by Intune when company data is removed, or when users are unenrolled from management. But, certificates aren't revoked on the certification authority.

## S/MIME email profiles

Once you have created S/MIME signing and encryption certificate profiles, you can [enable S/MIME for iOS/iPadOS native mail](../../device-configuration/templates/ref-email-settings-ios).