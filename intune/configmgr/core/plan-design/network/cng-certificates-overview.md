---
layout: Conceptual
title: CNG v3 certificates overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/cng-certificates-overview
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
description: Learn about support for Cryptography Next Generation (CNG) v3 certificates for Configuration Manager clients and servers.
ms.date: 2021-07-19T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 9e3033ee-1c86-a8af-dcce-6246142ca45f
document_version_independent_id: 1e2cc4d7-83cb-22c0-7a1b-3cfaf84a9f23
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/network/cng-certificates-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/network/cng-certificates-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/network/cng-certificates-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 24c43405-7b43-f4f4-5861-be3da8fa8525
---

# CNG v3 certificates overview - Configuration Manager | Microsoft Learn

Configuration Manager supports Cryptography: Next Generation (CNG) certificates. Configuration Manager clients can use a PKI client authentication certificate with the private key generated and stored in a CNG Key Storage Provider (KSP). With KSP support, Configuration Manager clients support hardware-based private keys, such as a TPM KSP for PKI client authentication certificates.

Note

When using CNG certificates, Configuration Manager clients only support certificates that use the **RSA** cryptographic algorithm. 

## Supported scenarios

You can use [Cryptography API: Next Generation (CNG)](/en-us/windows/win32/seccng/cng-features) v3 certificate templates for the following scenarios:

- Client registration and communication with an HTTPS management point
- Software distribution and application deployment with an HTTPS distribution point
- OS deployment
- Client messaging SDK (with latest update) and ISV Proxy
- Cloud management gateway (CMG) configuration
- User-targeted available applications in Software Center

Also use CNG v3 certificates for the following HTTPS-enabled server roles: 

- Management point
- Distribution point
- Software update point
- State migration point
- Certificate registration point, including the NDES server with the Configuration Manager policy module

Note

CNG is backward compatible with Crypto API (CAPI). CAPI certificates continue to be supported even when CNG support is enabled on the client.

## Unsupported scenarios

The following scenarios currently aren't supported:

- The following server roles aren't operational when installed in HTTPS mode with a CNG v3 certificate bound to the web site in Internet Information Services (IIS):

    - Enrollment point
    - Enrollment proxy point

## To use CNG certificates

To use CNG v3 certificates, your certification authority (CA) needs to provide CNG certificate templates for target machines. Template details vary according to the scenario; however, the following properties are required:

- **Compatibility** tab

    - **Certificate Authority** must be Windows Server 2008 or later. (Windows Server 2012 is recommended.)
    - **Certificate recipient** must be Windows Vista/Server 2008 or later. (Windows 8/Windows Server 2012 is recommended.)
- **Cryptography** tab

    - **Provider Category** must be **Key Storage Provider**. (required)
    - **Algorithm name** must be **RSA**. (required)
    - **Request must use one of the following providers:** must be **Microsoft Software Key Storage Provider**.

Note

The requirements for your environment or organization may be different. Contact your PKI expert. The important point to consider is a certificate template must use a Key Storage Provider to take advantage of CNG.

For best results, we recommend building the Subject Name from Active Directory information. Use the DNS Name for **Subject name format** and include the DNS name in the alternate subject name. Otherwise, you must provide this information when the device enrolls into the certificate profile.