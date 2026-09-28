---
layout: Conceptual
title: Certificates overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/certificates-overview
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
description: Learn about how Configuration Manager uses self-signed and PKI digital certificates.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 883c2b38-e1c9-cd1d-a805-90fbfad3f3df
document_version_independent_id: 7a387acc-4d7a-b45f-9926-9df63388358f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/security/certificates-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/security/certificates-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/security/certificates-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: d9a40ff1-bcbc-b262-cbbf-29be1bdbcd14
---

# Certificates overview - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager uses a combination of self-signed and public key infrastructure (PKI) digital certificates.

Use PKI certificates whenever possible. For more information, see [PKI certificate requirements](../network/pki-certificate-requirements). When Configuration Manager requests PKI certificates during enrollment for mobile devices, use Active Directory Domain Services and an enterprise certification authority. For all other PKI certificates, deploy and manage them independently from Configuration Manager.

PKI certificates are required when client computers connect to internet-based site systems. The cloud management gateway also requires certificates. For more information, see [Manage clients on the internet](../../clients/manage/manage-clients-internet).

When you use a PKI, you can also use IPsec to help secure the server-to-server communication between site systems in a site, between sites, and for other data transfer between computers. Implementation of IPsec is independent from Configuration Manager.

When PKI certificates aren't available, Configuration Manager automatically generates self-signed certificates. Some certificates in Configuration Manager are always self-signed. In most cases, Configuration Manager automatically manages the self-signed certificates, and you don't have to take another action. One example is the site server signing certificate. This certificate is always self-signed. It makes sure that the policies that clients download from the management point were sent from the site server and weren't tampered with. As another example, when you enable the site for [Enhanced HTTP](../hierarchy/enhanced-http), the site issues self-signed certificates to site server roles.

Important

Starting in Configuration Manager version 2103, sites that allow HTTP client communication are deprecated. Configure the site for HTTPS or Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](../../servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http).

## CNG v3 certificates

Configuration Manager supports *Cryptography: Next Generation* (CNG) v3 certificates. Configuration Manager clients can use a PKI client authentication certificate with private key in a CNG Key Storage Provider (KSP). With KSP support, Configuration Manager clients support hardware-based private keys, such as a TPM KSP for PKI client authentication certificates.

For more information, see [CNG v3 certificates overview](../network/cng-certificates-overview).

## Enhanced HTTP

Using HTTPS communication is recommended for all Configuration Manager communication paths, but is challenging for some customers because of the overhead of managing PKI certificates. The introduction of Microsoft Entra integration reduces some but not all of the certificate requirements. You can instead enable the site to use *enhanced HTTP*. This configuration supports HTTPS on site systems by using self-signed certificates, along with Microsoft Entra ID for some scenarios. It doesn't require PKI.

For more information, see [Enhanced HTTP](../hierarchy/enhanced-http).

## Certificates for CMG

Managing clients on the internet via the cloud management gateway (CMG) requires the use of certificates. The number and type of certificates varies depending upon your specific scenarios.

For more information, see [CMG set up checklist](../../clients/manage/cmg/set-up-checklist).

Note

The cloud-based distribution point (CDP) is deprecated. Starting in version 2107, you can't create new CDP instances. To provide content to internet-based devices, enable the CMG to distribute content. For more information, see [Deprecated features](../changes/deprecated/removed-and-deprecated-cmfeatures#deprecated-features).

For more information about certificates for a CDP, see [Certificates for the cloud distribution point](/en-us/previous-versions/troubleshoot/configmgr/use-a-cloud-based-distribution-point#bkmk_certs).

## The site server signing certificate

The site server always creates a self-signed certificate. It uses this certificate for several purposes.

Clients can securely get a copy of the site server signing certificate from Active Directory Domain Services and from client push installation. If clients can't get a copy of this certificate by one of these mechanisms, install it when you install the client. This process is especially important if the client's first communication with the site is with an internet-based management point. Because this server is connected to an untrusted network, it's more vulnerable to attack. If you don't take this other step, clients automatically download a copy of the site server signing certificate from the management point.

Clients can't securely get a copy of the site server certificate in the following scenarios:

- You don't install the client by using client push, and:

    - You haven't extended the Active Directory schema for Configuration Manager.
    - You haven't published the client's site to Active Directory Domain Services.
    - The client is from an untrusted forest or a workgroup.
- You're using internet-based client management and you install the client when it's on the internet.

For more information on how to install clients with a copy of the site server signing certificate, use the **SMSSIGNCERT** command-line property. For more information, see [About client installation parameters and properties](../../clients/deploy/about-client-installation-properties#smssigncert).

## Hardware-bound key storage provider

Configuration Manager uses self-signed certificates for client identity and to help protect communication between the client and site systems. When you update the site and clients to version 2107 or later, the client stores its certificate from the site in a hardware-bound key storage provider (KSP). This KSP is typically the trusted platform module (TPM) at least version 2.0. The certificate is also marked non-exportable.

If the client also has a PKI-based certificate, it continues to use that certificate for TLS HTTPS communication. It uses its self-signed certificate for signing messages with the site. For more information, see [PKI certificate requirements](../network/pki-certificate-requirements).

Note

For clients that also have a PKI certificate, the Configuration Manager console displays the **Client certificate** property as **Self-signed**. The client control panel **Client certificate** property shows **PKI**.

When you update to version 2107 or later, clients with PKI certificates will recreate self-signed certificates, but don't reregister with the site. Clients without a PKI certificate will reregister with the site, which can cause extra processing at the site. Make sure that your process to update clients allows for randomization. If you simultaneously update lots of clients, it may cause a backlog on the site server.

Configuration Manager doesn't use TPMs that are known vulnerable. For example, the TPM version is earlier than 2.0. If a device has a vulnerable TPM, the client falls back to using a software-based KSP. The certificate is still not exportable.

OS deployment media doesn't use hardware-bound certificates, it continues to use self-signed certificates from the site. You create the media on a device that has the console, but then it can run on any client.

To troubleshoot certificate behaviors, use the **CertificateMaintenance.log** on the client.