---
layout: Conceptual
title: Prerequisites for the Certificate Connector for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/certificates/connector/prerequisites
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
description: Review the software and network prerequisites for use of the Certificate Connector for Microsoft Intune.
ms.date: 2024-10-09T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: 6950f06a-ee49-9745-579f-3630f1d54bc7
document_version_independent_id: 6950f06a-ee49-9745-579f-3630f1d54bc7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/certificates/connector/prerequisites.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/certificates/connector/prerequisites
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/certificates/connector/prerequisites.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: ede4fe38-efd6-dfd4-e67a-2ea28012584f
---

# Prerequisites for the Certificate Connector for Microsoft Intune - Microsoft Intune | Microsoft Learn

Review the prerequisites and infrastructure requirements for the Certificate Connector for Microsoft Intune. Some prerequisites and infrastructure requirements can vary depending on the features you configure a connector instance to support.

## General prerequisites

Requirements for the computer where you install the connector software:

- Windows Server 2012 R2 or later.

Caution

Microsoft recommends enabling BitLocker (or an equivalent disk encryption solution) on the drive where the Certificate connector is installed. To learn more, see [BitLocker Overview:](/en-us/windows/security/operating-system-security/data-protection/bitlocker/).

    Note

    The Windows Server must be configured with the Desktop Experience, and for versions 2019 or earlier, the Microsoft Edge browser must be installed manually prior to initiating the connector setup. For more information, see [Install Server with Desktop Experience](/en-us/windows-server/get-started/getting-started-with-server-with-desktop-experience) in the Windows Server 2016 documentation.

    Important

    Strong mapping in the Microsoft Intune Certificate Connector is only supported for Windows Server version 2019 or later. For more information, see [Support tip: Implementing strong mapping in Microsoft Intune certificates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-implementing-strong-mapping-in-microsoft-intune-certificates/4053376).
- .NET 4.7.2
- Transport Layer Security (TLS) 1.2. For more information, see [Enable support for TLS 1.2 in your environment](/en-us/troubleshoot/azure/active-directory/enable-support-tls-environment) in the Microsoft Entra documentation.
- The server must meet the same network requirements as managed devices. See [Network endpoints for Microsoft Intune](../../endpoints).
- To support automatic updates of the connector software, the server must have access to the **Azure update service**:

    - Port: **443**
    - Endpoint: **autoupdate.msappproxy.net**
- The **Enhanced Security Configuration** must be deactivated.

## PKCS

Requirements for private and public key pair (PKCS) certificate templates:

- Certificate templates that you use for PKCS requests must be configured with permissions that allow the certificate connector service account to enroll the certificate.
- The certificate templates must be added to the Certification Authority (CA).

Note

Any instance of the connector that supports PKCS can be used to retrieve pending PKCS requests from the Intune Service queue, process Imported certificates, and handle revocation requests. It's not possible to define which connector handles each request.  Therefore, each connector that supports PKCS must have the same permissions and be able to connect with all the certification authorities defined later in the PKCS profiles.

## PKCS imported certificates

To support PKCS imported certificates, the server that hosts the connector requires additional configurations, such as configuring a Key storage provider access to allow the Connector Service User to retrieve keys.

For information about support for PKCS imported certificates, see [Configure and use imported PKCS certificates with Intune](../../../device-configuration/certificates/imported-pfx-profiles).

## Revocation Prerequisites

- The Certification Authority must be configured to allow the connector service account to revoke certificates.

## SCEP

To support Simple Certificate Enrollment Protocol (SCEP) certificates, the Windows Server that hosts the connector must meet the following prerequisites in addition to the general prerequisites:

- IIS 7 or higher
- Network Device Enrollment Service (NDES) service, which is part of the Active Directory Certification Services role. The connector isn't supported on the same server as your issuing Certification Authority (CA). For more information, see [Configure infrastructure to support SCEP with Intune](../scep-infrastructure).

On the Windows Server, select to add the following Server Roles and Features:

- **Server Roles**:

    - Active Directory Certificate Services
    - Web Server (IIS)
- **Features**:

    - .NET Framework 4.7 Features
        - .NET Framework 4.7
        - ASP.NET 4.7
        - WCF Services
            - HTTP Activation
- **AD CS &gt; Role Services**:

    - Network Device Enrollment Service - For the connector SCEP when you use a Microsoft CA, [install, and configure](../scep-infrastructure#set-up-ndes) the **Network Device Enrollment Service** (NDES) server role. When you configure NDES, you need to assign a user account for use by the NDES application pool. NDES also has its own requirements.
- **Web Server Role (IIS) &gt; Role Services**:

    - Security
        - Request Filtering
    - Application Development
        - .NET Extensibility 4.7
        - ASP.NET 4.7
    - Management Tools
        - IIS Management Console
        - IIS 6 Management Compatibility
            - IIS 6 Metabase Compatibility
            - IIS 6 WMI Compatibility

    In addition, NDES requires the following.NET Framework 3.5 Features:

    - .NET Framework 3.5
    - HTTP Activation

Requirements for SCEP certificate templates:

- Certificate templates you use for SCEP requests must be configured with permissions that allow the Certificate Connector service account to auto enroll the certificate.
- The certificate templates must be added to the CA.

## Accounts

Prepare the following accounts before you install the certificate connector software.

### Installation account

You can use any user account that has local administrative permissions on the Windows Server to install the connector software. You can use this same account to configure the Windows Server with the NDES Windows server role should you use SCEP and a Microsoft CA.

### Certificate connector service account

The certificate connector requires an account to use as a service account. This account is used by the connector to access the Windows Server, communicate with Intune, and access the Certification Authority to service PKI requests.

The connector service account must have the following permissions:

- [**Logon as Service**](/en-us/system-center/scsm/enable-service-log-on-sm?view=sc-sm-2019&amp;preserve-view=true)
- **Issue and Manage Certificates** permissions on the Certification Authority (required only for revocation scenarios).
- **Read** and **Enroll** permissions on any certificate template that you use to issue certificates.
- Permissions to the **Key Storage Provider** (KSP) that's used by PFX Import. See [Import PFX Certificates to Intune](../../../device-configuration/certificates/imported-pfx-profiles#import-pfx-certificates).

The following options are supported for use as the certificate connector service account:

- **SYSTEM**
- **Domain user** - Use any domain user account that is an administrator on the Windows Server.

For more information, see [Install the Certificate Connector for Microsoft Intune](setup-connector).

### NDES application pool user

To use SCEP with a Microsoft CA, you need to add NDES to the server that hosts the connector before installing the connector. When you configure NDES, you need to specify an account for use as the application pool user, which can also be referred to as the NDES service account. This account can be a local or domain user account and must have the following permissions:

- **Read** and **Enroll** permissions on each SCEP certificate template you use to issue certificates.
- Member of the **IIS\_IUSRS** group.

For guidance on configuring the NDES server role for the Certificate Connector for Microsoft Intune, see [Set up NDES](../scep-infrastructure#set-up-ndes) in **Configure infrastructure to support SCEP with Intune**.

### Microsoft Entra user

When configuring the connector, use a user account that is the built-in **[Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** Microsoft Entra role and has an Intune license assigned.